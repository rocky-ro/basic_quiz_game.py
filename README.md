class Quiz:
    def __init__(self, questions):
        self.questions = questions
        self.score = 0
    
    def display_question(self, question):
        print(question['question'])
        for i, option in enumerate(question['options'], 1):
            print(f"{i}. {option}")
    
    def validate_answer(self, question, user_answer):
        correct_answer = question['answer']
        if user_answer.lower() == correct_answer.lower():
            print("Correct!")
            self.score += 1
        else:
            print(f"Incorrect! The correct answer is: {correct_answer}")
    
    def start_quiz(self):
        for question in self.questions:
            self.display_question(question)
            user_input = input("Enter the number of your answer: ")
            while not user_input.isdigit() or int(user_input) not in range(1, len(question['options']) + 1):
                print("Invalid input. Please enter a number between 1 and", len(question['options']))
                user_input = input("Enter the number of your answer: ")
            self.validate_answer(question, question['options'][int(user_input) - 1])
            print()
        print(f"Quiz complete! You got {self.score} out of {len(self.questions)} correct.")

# Define questions with options and answers
questions = [
    {
        "question": "What is the capital of France?",
        "options": ["Paris", "London", "Berlin", "Rome"],
        "answer": "Paris"
    },
    {
        "question": "What is 2 + 2?",
        "options": ["3", "4", "5", "6"],
        "answer": "4"
    },
    {
        "question": "What is the largest mammal?",
        "options": ["Elephant", "Giraffe", "Blue whale", "Lion"],
        "answer": "Blue whale"
    }
]

# Create quiz instance and start the quiz
quiz = Quiz(questions)
quiz.start_quiz()
