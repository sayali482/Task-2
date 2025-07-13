from flask import Flask, render_template, request
import requests

app = Flask(__name__)
API_KEY = "your_api_key_here"  # 🔑 Replace this with your OpenWeatherMap API key

def get_weather(city):
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_KEY}&units=imperial"
    response = requests.get(url)
    return response.json()

@app.route('/', methods=['GET', 'POST'])
def index():
    weather = None
    forecast = []
    if request.method == 'POST':
        city = request.form['city']
        weather = get_weather(city)

        # Dummy 5-day forecast
        forecast = [
            {"date": "Dec 21st", "temp": 47.1, "humidity": 81},
            {"date": "Dec 22nd", "temp": 47.5, "humidity": 82},
            {"date": "Dec 23rd", "temp": 49.0, "humidity": 86},
            {"date": "Dec 24th", "temp": 52.8, "humidity": 79},
            {"date": "Dec 25th", "temp": 55.7, "humidity": 75}
        ]

    return render_template('index.html', weather=weather, forecast=forecast)

if __name__ == '__main__':
    app.run(debug=True)