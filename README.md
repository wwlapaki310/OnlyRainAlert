# OnlyRainAlert ☔️

A simple and fast React Native app that sends morning notifications only on rainy days.

## 🏗️ System Architecture

```mermaid
graph TB
    User[👤 User] --> App[📱 OnlyRainAlert App]
    
    subgraph "React Native App"
        App --> UI[🎨 UI Components]
        App --> Location[📍 Location Service]
        App --> Weather[🌦️ Weather Service]
        App --> Notification[🔔 Notification Service]
        App --> Storage[💾 Local Storage]
        App --> I18n[🌍 Internationalization]
    end
    
    subgraph "External Services"
        WeatherAPI[🌤️ Weather API<br/>OpenWeatherMap]
        GPS[🛰️ GPS/Location Services]
    end
    
    subgraph "Device Features"
        LocalNotification[📲 Local Notifications]
        DeviceLocation[📍 Device GPS]
    end
    
    Location --> DeviceLocation
    Location --> GPS
    Weather --> WeatherAPI
    Notification --> LocalNotification
    
    subgraph "Data Flow"
        Morning[⏰ Morning Timer] --> CheckWeather{🌧️ Rain Check}
        CheckWeather -->|Rain Expected| SendNotification[🔔 Send Alert]
        CheckWeather -->|No Rain| NoAction[✅ No Action]
    end
    
    Storage --> UserSettings[⚙️ User Settings<br/>• Notification Time<br/>• Location<br/>• Language]
    
    style App fill:#e1f5fe
    style WeatherAPI fill:#fff3e0
    style LocalNotification fill:#f3e5f5
    style Morning fill:#e8f5e8
```

## 🔄 Data Flow

```mermaid
sequenceDiagram
    participant U as User
    participant A as OnlyRainAlert
    participant L as Location Service
    participant W as Weather API
    participant N as Notification System
    
    U->>A: Opens App
    A->>L: Request Location Permission
    L->>A: Grant Permission
    A->>L: Get Current Location
    L->>A: Return Coordinates
    
    Note over A: Daily at Set Time (e.g., 06:00)
    A->>W: Request Weather Forecast
    W->>A: Return Weather Data
    
    alt Rain Expected
        A->>N: Schedule Rain Notification
        N->>U: 🌧️ "Rain expected today!"
    else No Rain
        Note over A: No notification sent
    end
    
    U->>A: Change Settings
    A->>A: Save to Local Storage
```

## 🌟 Features

- **Simple & Fast**: Minimal design with optimal performance
- **Smart Notifications**: Only notifies when rain is expected in your area
- **Customizable Time**: Set your preferred morning notification time (default: 06:00)
- **Global Support**: Works worldwide with local weather data
- **Free to Use**: Basic functionality available at no cost
- **Monetization Ready**: Premium features for enhanced experience

## 📱 Screenshots

_Coming soon..._

## 🛠️ Tech Stack

- **React Native**: Cross-platform mobile development
- **Weather API**: Real-time weather data integration (OpenWeatherMap)
- **Push Notifications**: Local notification system
- **Internationalization**: Multi-language support (i18next)
- **Location Services**: GPS-based location detection
- **Local Storage**: AsyncStorage for user preferences

## 🚀 Getting Started

### Prerequisites

- Node.js (v16 or higher)
- React Native CLI
- Android Studio / Xcode

### Installation

```bash
# Clone the repository
git clone https://github.com/wwlapaki310/OnlyRainAlert.git

# Navigate to project directory
cd OnlyRainAlert

# Install dependencies
npm install

# For iOS
cd ios && pod install

# Run the app
npx react-native run-android
# or
npx react-native run-ios
```

## 📋 Development Roadmap

See [Issues](https://github.com/wwlapaki310/OnlyRainAlert/issues) for detailed development tasks.

## 🌍 Supported Languages

- English
- 日本語 (Japanese)
- More languages coming soon...

## 💡 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Support

For support, please create an issue in this repository.

---

**Built with ❤️ for people who want to stay dry** 🌂