# Synthesizer Prototype - Two-Screen Setup

A two-screen interactive synthesizer where your phone acts as a controller and your laptop displays the animations in real-time.

## Features

- 40 pressable keys
- Real-time WebSocket communication between devices
- Phone controller with touch-friendly interface
- Laptop display with animated key responses
- 2px downward shift animation when keys are pressed

## Setup Instructions

### 1. Install Dependencies

Make sure you have Node.js installed, then run:

```bash
npm install
```

### 2. Start the Server

```bash
npm start
```

The server will start on port 3000. You should see:
```
Server running at http://localhost:3000/
Display (laptop): http://localhost:3000/display.html
Controller (phone): http://localhost:3000/phone.html
```

### 3. Find Your Laptop's IP Address

On your laptop, find your local IP address:

**Mac/Linux:**
```bash
ifconfig | grep "inet " | grep -v 127.0.0.1
```

**Windows:**
```bash
ipconfig
```

Look for your local IP address (usually starts with 192.168.x.x or 10.0.x.x)

### 4. Open on Laptop (Display)

On your laptop, open a web browser and go to:
```
http://localhost:3000/display.html
```

This will show the synthesizer display that reacts to key presses from your phone.

### 5. Open on Phone (Controller)

On your phone, make sure you're connected to the **same WiFi network** as your laptop.

Open a web browser and go to:
```
http://[YOUR-LAPTOP-IP]:3000/phone.html
```

Replace `[YOUR-LAPTOP-IP]` with your laptop's IP address from step 3.

For example: `http://192.168.1.100:3000/phone.html`

### 6. Start Playing!

- Press keys on your phone
- Watch the animations appear on your laptop screen
- The keys will shift down 2px when pressed and return when released

## Troubleshooting

### Phone can't connect to laptop

1. Make sure both devices are on the same WiFi network
2. Check that your firewall isn't blocking port 3000
3. Verify the IP address is correct

### Connection status

- **Phone**: Check the status indicator at the top of the screen
  - Green "Connected ✓" = Working
  - Red "Disconnected" or "Connection Error" = Problem

- **Laptop**: Open browser console (F12) to see connection status

### Port already in use

If port 3000 is already in use, edit `server.js` and change:
```javascript
const PORT = 3000;
```
to another port number (e.g., 3001), then update your URLs accordingly.

## Files

- `server.js` - WebSocket server for device communication
- `display.html` - Laptop display interface
- `phone.html` - Phone controller interface
- `synthesizer svg` - SVG file with synthesizer graphics
- `package.json` - Node.js dependencies

## Technical Details

- WebSocket server using `ws` library
- Real-time bidirectional communication
- Touch-optimized mobile interface
- 8x5 grid layout for 40 keys on phone
- Animated key press effects with CSS transforms
