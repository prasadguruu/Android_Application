# ChitChat - Modern Android Chat Application



## Overview

ChitChat is a modern, real-time chat application built for Android using Jetpack Compose and Firebase. It features a clean, Material 3 design with Target's brand colors and provides a seamless messaging experience.

## Features

### Authentication
- Email/Password authentication
- Google Sign-In integration
- Email verification
- Secure authentication state management

### Messaging
- Real-time one-on-one chat
- Group chat functionality
- Message status indicators (sent/seen)
- Offline message support
- Real-time typing indicators

### User Management
- User profiles with customizable display names and bios
- Online/Offline status indicators
- Last seen timestamps
- User search functionality
- Profile verification badges

### UI/UX
- Material 3 design language
- Target brand color scheme (Red #CC0000)
- Dark/Light theme support
- Responsive and adaptive layouts
- Smooth animations and transitions

### Technical Features
- Real-time data synchronization
- Offline data persistence
- Firebase Cloud Messaging integration
- Efficient data caching
- Automatic user cleanup system

## Technology Stack

- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Architecture**: MVVM
- **Backend**: Firebase
  - Authentication
  - Realtime Database
  - Cloud Messaging
- **Dependencies**:
  - AndroidX Core KTX
  - Compose BOM
  - Material 3
  - Firebase BOM
  - Google Play Services Auth
  - WorkManager

## Getting Started

### Prerequisites
- Android Studio Arctic Fox or later
- JDK 11 or later
- Android SDK 24 or later
- Google Play Services

### Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/chit_chat.git
   ```

2. Open the project in Android Studio

3. Create a Firebase project and add your `google-services.json` file to the app directory

4. Configure Firebase:
   - Enable Authentication (Email/Password and Google Sign-In)
   - Set up Realtime Database
   - Configure Firebase Cloud Messaging

5. Build and run the application

### Firebase Database Rules
Add these security rules to your Firebase Realtime Database:
```json
{
  "rules": {
    "users": {
      ".read": "auth != null",
      "$uid": {
        ".write": "auth != null && auth.uid == $uid"
      }
    },
    "chats": {
      "$chatId": {
        ".read": "auth != null && ($chatId.matches(/.*-.*/) && ($chatId.matches(concat(auth.uid, '-.*')) || $chatId.matches(concat('.*-', auth.uid))))",
        ".write": "auth != null && ($chatId.matches(/.*-.*/) && ($chatId.matches(concat(auth.uid, '-.*')) || $chatId.matches(concat('.*-', auth.uid))))"
      }
    }
  }
}
```

## Architecture

The application follows the MVVM (Model-View-ViewModel) architecture pattern and is organized into the following main components:

```
app/
├── data/
│   ├── models/
│   └── repositories/
├── firebase/
│   └── FirebaseHelper.kt
├── ui/
│   ├── screens/
│   ├── theme/
│   └── viewmodels/
└── ChitChatApplication.kt
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Material Design 3 Guidelines
- Firebase Documentation
- Jetpack Compose Documentation
- Target Brand Guidelines

