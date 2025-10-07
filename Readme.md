# SkillSync 🚀

A comprehensive collaboration platform connecting learners, mentors, and project teams. SkillSync empowers users to discover talent, collaborate on projects, and grow together through skill-based matching and real-time communication. ✨

## Overview 🎯

SkillSync is a mobile-first platform designed to bridge the gap between learners seeking opportunities and project owners looking for talent. Whether you're a beginner looking to gain experience, a mentor willing to guide others, or a project owner building a team, SkillSync provides the tools to connect and collaborate effectively. 🤝

## Key Features 🌟

### User Management 👥 👤
- **Authentication & Authorization**: Secure signup and login with JWT-based authentication 🔐
- **Email Validation**: Real-time email verification using EmailValidation.io API ✅
- **Profile Management**: Comprehensive user profiles with skills, experience level, location, and bio 📝
- **Mentor System**: Users can register as mentors to guide and support learners 🎓

### Project Management 📋 📊
- **Project Creation**: Create and manage projects with custom requirements 🛠️
- **Team Building**: Set team size, required skills, and project domains 👥
- **Public/Private Projects**: Control project visibility 🔒
- **Application System**: Users can apply to join projects 📬
- **Invitation System**: Project owners can invite specific users to join 💌
- **Slot Management**: Automatic tracking of available team positions 🎯

### Collaboration Features 🤝
- **Real-time Notifications**: Socket.io-powered instant notifications for: 🔔
  - Project invitations
  - Application submissions
  - Application acceptances/rejections
  - Invitation responses
- **Team Member Management**: View and manage project team members 👨‍💼
- **Smart Matching**: Skill-based discovery to find the right teammates 🎯

### Q&A Platform 💬
- **Question Posting**: Users can post domain-specific questions ❓
- **Answer System**: Mentors and peers can provide answers 💡
- **Knowledge Sharing**: Browse questions and answers from the community 📚

### User Discovery 🔍
- **Search Functionality**: Find users based on skills, experience, and availability 🔎
- **Mentor Discovery**: Dedicated mentor listing 👨‍🏫
- **Teammate Availability**: See who's actively looking for collaborations ✨

## Tech Stack 💻

### Frontend 📱
- **React Native**: Cross-platform mobile development
- **React Navigation**: Seamless navigation experience

### Backend ⚙️
- **Node.js**: Server-side runtime
- **Express.js**: Web application framework
- **MongoDB**: NoSQL database for flexible data storage
- **Mongoose**: ODM for MongoDB

### Authentication & Security 🔐
- **JWT (jsonwebtoken)**: Secure token-based authentication
- **bcryptjs**: Password hashing and encryption

### Real-time Communication ⚡
- **Socket.io**: Bidirectional event-based communication
- **WebSocket**: Real-time notification delivery

### External Services 🌐
- **EmailValidation.io API**: Email verification service

## API Endpoints 🛣️

### Authentication 🔑
```
POST /api/auth/signup - User registration
POST /api/auth/login - User login
```

### User Management
```
GET /api/users - Get all users
GET /api/users/:loggedInUserId/except - Get all users except logged-in user
GET /api/users/:userId - Get user by ID
GET /api/mentors - Get all mentors
PUT /api/users/:userId/profile - Update user profile
```

### Project Management
```
POST /api/projects/:userId - Create new project
GET /api/projects/my/:userId - Get user's projects
GET /api/projects/public/:userId - Get user's public projects
GET /api/projects/:projectId/members - Get project members
POST /api/projects/apply - Apply for a project
POST /api/projects/invite - Send project invitation
POST /api/projects/accept-invite - Accept project invitation
POST /api/projects/accept-application - Accept user application
```

### Notifications 🔔
```
GET /api/notifications/:userId - Get user notifications
PUT /api/notifications/:notificationId/status - Update notification status
PUT /api/notifications/:notificationId/read - Mark notification as read
DELETE /api/notifications/:notificationId - Delete notification
```

### Q&A System 💬
```
POST /api/questions - Add a new question
GET /api/questions - View all questions
GET /api/questions/:questionId/answers - View answers for a question
POST /api/questions/:questionId/answers - Add an answer to a question
```

## Database Models 🗄️

### User Schema 👤
- Personal information (username, email, fullName)
- Professional details (skills, experience level, location)
- Profile metadata (avatar, bio, LinkedIn)
- Collaboration preferences (lookingForTeammates, availableForHackathons)
- Mentor status
- Associated projects and notifications

### Project Schema 📁
- Project details (title, description, domain)
- Team configuration (teamSize, availableSlots, members)
- Requirements (requiredSkills)
- Visibility (isPublic)
- Applications and invitations tracking
- Deadline management

### Notification Schema 📬
- Notification type (application, invite, response)
- Sender and receiver references
- Associated project
- Status tracking (pending, accepted, rejected)
- Read status

### Question Schema ❓
- Question content and domain
- Seeker reference
- Answers array with responder references
- Timestamps

## Environment Variables ⚙️

Create a `.env` file in the root directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=your_mongodb_connection_string

# Authentication
JWT_SECRET=your_jwt_secret_key

# Email Validation
MAIL_API_KEY=your_emailvalidation_api_key
```

## Installation & Setup 🚀

### Prerequisites ✅
- Node.js (v14 or higher)
- MongoDB
- npm or yarn
- React Native development environment

### Backend Setup 🔧

1. Clone the repository:
```bash
git clone https://github.com/riddhilahare14/SkillSync.git
cd SkillSync
```

2. Install dependencies:
```bash
npm install
```

3. Configure environment variables:
```bash
cp .env.example .env
# Edit .env with your configuration
```

4. Start the server:
```bash
npm start
```

### Frontend Setup 📱

1. Navigate to the mobile app directory:
```bash
cd mobile
```

2. Install dependencies:
```bash
npm install
```

3. For iOS (Mac only):
```bash
cd ios && pod install && cd ..
```

4. Run the app:
```bash
# For iOS
npm run ios

# For Android
npm run android
```

## Key Features Implementation 🎨

### Email Validation ✉️
Real-time email verification ensures valid user registrations and reduces fake accounts using the EmailValidation.io API.

### Smart Notification System 🔔
The platform uses Socket.io for instant notifications with automatic status updates and cleanup of processed notifications.

### Flexible Project Management 🎯
Projects support both application-based and invitation-based team building, with automatic slot management to prevent overbooking.

### Authorization Controls 🛡️
Multi-level authorization ensures:
- Only project owners can send invitations
- Only receivers can respond to notifications
- Proper validation of all user actions

## Security Features 🔒

- Password hashing with bcrypt 🔐
- JWT-based authentication 🎫
- Input validation and sanitization ✅
- Protected API endpoints 🛡️
- Email verification 📧
- Secure notification deletion with authorization checks 🔑

## Error Handling ⚠️

Comprehensive error handling across all controllers with:
- Detailed error logging 📝
- User-friendly error messages 💬
- Appropriate HTTP status codes 🔢
- Validation checks for all inputs ✔️

## Future Enhancements 🔮

- File sharing and document collaboration 📎
- Video chat integration for team meetings 🎥
- Advanced project search and filtering 🔍
- Rating and review system ⭐
- Achievement badges and gamification 🏆
- In-app messaging system 💬
- Calendar integration for deadlines 📅
- Project templates 📋

## Contact 📧

**Riddhi Lahare**
- GitHub: [@riddhilahare14](https://github.com/riddhilahare14) 💻
- Project Link: [https://github.com/riddhilahare14/SkillSync](https://github.com/riddhilahare14/SkillSync) 🔗

## Acknowledgments 🙏

- React Native community for excellent documentation 📱
- MongoDB for flexible data modeling 🍃
- Socket.io for real-time communication capabilities ⚡
- EmailValidation.io for email verification services ✅

---

Made with ❤️ and lots of ☕ during our College PBL journey 🚀
