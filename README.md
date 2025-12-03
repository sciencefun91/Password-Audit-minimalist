A Simple and Essential Website by Simone Pederzolli  

Video Demo: https://youtu.be/S2v-enejSV4

## Description  
This final project involves developing a website dedicated to password security. I selected this topic because it represents a fundamental aspect of cybersecurity that is frequently overlooked despite its importance.

The website is fully responsive and has been tested on PCs, tablets, and mobile devices. The project folder contains:  
- Three HTML pages for the main site structure  
- A CSS file for styling and layout  
- A favicon and two images  

## Structure  

### Navigation Bar  
A fixed navigation bar at the top provides access to the three main sections: **Home**, **Tools**, and **Contact**.

### Home Page  
This section introduces the project's purpose and provides an overview. It explains the core functionality available in the Tools section, discusses common password mistakes, and concludes with key takeaways about password security.

### Security Tools (Core Functionality)  
This page contains two main interactive tools:  

1. **Password Compromise Check**  
Technical Implementation Details:
The password check operates through a carefully implemented client-side process. When a user submits a password, JavaScript's Web Crypto API first converts it to a SHA-1 hash. This hash is then split: only the first 5 characters (the prefix) are transmitted to the Have I Been Pwned API. This k-anonymity approach ensures that no complete password information leaves the user's browser. The API responds with a list of hundreds of password suffixes that share that same 5-character prefix. My JavaScript then performs a local comparison to see if the remaining 35 characters of the user's hash match any in the returned list.

Error Handling and User Experience:
I implemented comprehensive error handling to manage various scenarios. Network timeouts are handled gracefully with user-friendly messages if the API doesn't respond within 10 seconds. Invalid API responses trigger appropriate warnings without crashing the interface. The system also validates input before processing—empty passwords are rejected immediately, and excessively long inputs are truncated to prevent performance issues. For user convenience, I included sample test passwords ("password123" as compromised and "CS50final2025!" as safe) that users can try with a single click to understand the tool's functionality without entering personal passwords.

Privacy and Security Considerations:
This implementation prioritizes privacy through several mechanisms. No passwords are stored locally or transmitted in plaintext. The temporary hash comparison happens in memory and isn't persisted to disk. The interface clears password fields after checking and doesn't maintain a history of checked passwords. Additionally, the tool includes educational explanations about why password exposure matters and what steps users should take if their password appears in a breach.

Performance Optimizations:
To ensure responsive performance, I implemented request debouncing that waits for users to stop typing before initiating the API call. A visual loading indicator provides feedback during the approximately 1-2 second checking process. The code efficiently parses the API's response (which can contain hundreds of lines) using optimized string matching algorithms to quickly determine match status even on mobile devices with limited processing power.

2. **Secure Password Generator**  
Implementation Details:
The password generator uses different algorithms for each password type. Memorable passwords combine random words with numbers for better recall. Fully random passwords use secure cryptographic functions. The strength meter checks length, character variety, and common patterns to give a security score from 0 to 10.

User Features:
Users can adjust password length with a slider from 8 to 64 characters. Each password type has clear explanations of best use cases. The copy button works on all modern browsers. Password history is saved during the session so users can return to previous passwords.

Technical Choices:
I chose client-side generation to keep passwords private. The algorithms avoid predictable patterns while maintaining true randomness. The code is modular so new password types can be added easily. All generation happens instantly without server calls.

Testing & Validation:
The generator was tested across different password lengths and types. Each algorithm was verified to produce truly random outputs. The strength indicator was calibrated against known password security guidelines to ensure accurate scoring.

### Contact Page  
This section provides my contact information (email, phone, and address) along with an embedded Google Maps view of my location in Riva del Garda, Italy. A contact form allows visitors to send messages directly to my email.

## Technical Implementation  
The website uses:  
- HTML5 for structure  
- CSS3 with Bootstrap for responsive design  
- JavaScript for interactive functionality  
- External APIs (Have I Been Pwned) for password checking  

## Development Notes  
This project emphasizes practical functionality over visual design, focusing on implementing usable security tools. During development, I used AI assistance for code review and optimization. Importantly, I avoided being a "prompt monkey" (blindly copying code); instead, I used AI as a learning tool to understand better practices and improve my own coding skills.

As a beginner in web development, this project represents my effort to create something both educational and practical in the field of cybersecurity.
