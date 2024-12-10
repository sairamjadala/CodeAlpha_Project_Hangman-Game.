import random
def select_random_word():
    words = ["python", "hangman", "developer", "programming", "challenge", "algorithm", "lucky", "luxury", "lymph"]
    return random.choice(words)

def display_word(word, guessed_letters):
    return " ".join([letter if letter in guessed_letters else "_" for letter in word])

def hangman():
    print("Welcome to Hangman!")
    word = select_random_word()
    guessed_letters = set()
    incorrect_guesses = 0
    max_attempts = 6  # Set the limit on incorrect guesses

    print("The word has", len(word), "letters.")
    
    while incorrect_guesses < max_attempts:
        print("\nCurrent word:", display_word(word, guessed_letters))
        print("Guessed letters:", " ".join(sorted(guessed_letters)))
        print(f"Incorrect guesses left: {max_attempts - incorrect_guesses}")
        guess = input("Guess a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single valid letter.")
            continue
        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue
        guessed_letters.add(guess)
        if guess in word:
            print("Good guess!")
        else:
            print("Wrong guess!")
            incorrect_guesses += 1

        if all(letter in guessed_letters for letter in word):
            print("\nCongratulations! You've guessed the word:", word)
            break
    else:
        print("\nSorry, you've run out of attempts. The word was:", word)
# let us Start the game
hangman()
