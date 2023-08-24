import telebot
import webbrowser
from telebot import types

bot = telebot.TeleBot('6658127649:AAFRWJ1KpBoXGMNtKoonzorVu2UFymVpi0k')

@bot.message_handler(commands=['site'])
def site(message):
    webbrowser.open('https://project4511891.tilda.ws')

@bot.message_handler(commands=['start'])
def start(message):
    markup = types.ReplyKeyboardMarkup()
    btn1 = types.KeyboardButton('Товары📦')
    markup.row(btn1)
    btn2 = types.KeyboardButton('Перейти на Веб Сайт🌐')
    btn3 = types.KeyboardButton('Информация📚')
    markup.row(btn2, btn3)
    bot.send_message(message.chat.id, 'Здравствуйте, {0.first_name}!'.format(message.from_user), reply_markup=markup)
    bot.register_next_step_handler(message, on_click)

@bot.message_handler(content_types=['text'])
def on_click(message):
    if message.text == 'Товары📦':
        file = open('./sumkakb1.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Рюкзак Бирюзовый Kiber One')
        file = open('./ruchka.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Шариковая ручка')
        file = open('./noski.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Носки айтишника')
        file = open('./nakleyki.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Набор наклеек')
        file = open('./kepka.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Черная бейсболка')
        file = open('./futbolka.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Фирменная футболка ')
        file = open('./fleshka.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Вместительная флешка')
        file = open('./braslet.jpg', 'rb')
        bot.send_photo(message.chat.id, file, 'Силиконовый браслет')

    elif message.text == 'Перейти на Веб Сайт🌐':
        webbrowser.open('https://project4511891.tilda.ws')

    elif message.text == 'Информация📚':
        bot.send_message(message.chat.id, "1. Чтобы узнать полее подробную информацию о каждом товаре, перейдите на наш сайт.")

        bot.send_message(message.chat.id, '2. Все покупки совершаются нашей внутренней валютой - Киберонами.')

        bot.send_message(message.chat.id, "3. Кибероны нельзя купить, но можно заработать.")

        bot.send_message(message.chat.id, '4. Кибероны зачисляются за посещение занятий, а так же по другим причинам, подробнее можно узнать на сайте.')

        bot.send_message(message.chat.id, '5. Не хотите делать покупки через интернет? Мы проводим ярмарку у нас в здании 2 раза в год!')

    else:
        bot.send_message(message.chat.id, 'Я могу отвечать только на определенные сообщения😣')

@bot.message_handler(content_types=['audio', 'video', 'photo'])
def media(message):
    bot.send_message(message.chat.id, 'Я не умею читать медиа файлы😕')

bot.polling(none_stop=True)
