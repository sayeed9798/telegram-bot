import telebot  # Import the Telegram bot library
import re  # Import regex (pattern matching) library to find numbers in the text

# Replace 'YOUR_BOT_TOKEN' with the token you got from BotFather
bot = telebot.TeleBot("7010956607:AAGIPJGuF0UIlyR93HOzYTs2HSL5ulphGwU", parse_mode='HTML')  # Set parse_mode to HTML for bold text and clickable links

# Function to extract numbers and generate links
def generate_links(text):
    # Find 11 or 12-digit numbers in the input text
    numbers = re.findall(r"\b\d{11,12}\b", text)

    # Generate links from these numbers but format them to "Click Here" style
    links = [f'<a href="https://www.tatasteel.co.in/wcmvendor/PrintPermit.aspx?PTW={num}">Click Here for E-permit Sheet</a>' for num in numbers]

    # If links are found, return them with a message; otherwise, return an error message
    if links:
        return "Please Click on below link to get your E-permit Data, thanks:\n\n" + "\n".join(links)
    else:
        return "No valid permit numbers found."

# This function handles any message sent to the bot
@bot.message_handler(func=lambda message: True)
def handle_message(message):
    username = message.from_user.first_name  # Get the user's first name
    response = generate_links(message.text)  # Generate links from the message text

    # Add the user's name to the response
    custom_response = f"Hey {username}, {response}"
    
    bot.reply_to(message, custom_response)  # Reply to the user with the generated links

# Start the bot
print("Bot is running...")  # Print message when the bot starts
bot.polling()  # Keep the bot running and listening for messages
