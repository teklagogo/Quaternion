# Quaternion 3D to 2D Motion Mapping

An interactive web app that shows how 3D quaternion rotations map to 2D screen coordinates. Perfect for understanding mobile device motion control.

## What It Does

This tool visualizes the math behind motion-controlled interfaces. When you tilt your phone and a cursor moves on screen, quaternion math is doing the heavy lifting. This app breaks it down visually.

Great for:
- Mobile app developers working with device orientation
- AR/VR projects
- Mobile game development
- Anyone learning quaternions and 3D math

## Features

**3D Phone Model** - Rotates in real-time as you adjust quaternion values. Smooth CSS 3D transforms show roll, pitch, and yaw.

**2D Screen Mapping** - Grid with animated cursor showing the mapped position. See exactly how 3D rotation becomes 2D movement.

**Quaternion Controls** - Four sliders for w, x, y, z components. Auto-normalization keeps everything stable.

**Live Math Display** - Real-time quaternion values, Euler angles, and screen coordinates.

**Animation Mode** - Automatic rotation demo with smooth sinusoidal motion.

## How It Works

1. **Quaternions** represent 3D rotations without gimbal lock
2. **Convert** to Euler angles (roll, pitch, yaw) 
3. **Map** pitch to Y-axis and yaw to X-axis for screen coordinates

The mapping is intuitive: pitch forward = cursor up, yaw left = cursor left. Roll only affects visual rotation.

## Usage

Just open the HTML file in any modern browser. No build process needed.

- **Sliders**: Adjust quaternion components (-1 to 1)
- **Reset**: Return to identity quaternion (1,0,0,0)
- **Animate**: Start/stop auto-rotation demo

## Real-World Example

```javascript
// Device orientation to cursor control
window.addEventListener('deviceorientation', (event) => {
    const quaternion = eulerToQuaternion(event.alpha, event.beta, event.gamma);
    const screenPos = mapQuaternionToScreen(quaternion);
    updateCursorPosition(screenPos.x, screenPos.y);
});
```
## Customization

Change colors and sizes with CSS variables:

```css
:root {
    --primary-color: #3b82f6;
    --phone-size: 80px;
    --screen-bounds: 200px;
}
```

## Modify motion sensitivity:

``` javascriptconst screenX = euler.yaw * SENSITIVITY_X;
const screenY = -euler.pitch * SENSITIVITY_Y;
```
## Common Issues

**Cursor stuck:** Quaternion values might need normalization
**No 3D effects:** Browser may not support CSS 3D transforms
**Debug mode:** Use console.log('Q:', mapper.quaternion) to check values

## Compatibility
Runs on Chrome, Firefox, Safari, and Edge. Mobile-friendly responsive design.
##
Pure HTML/CSS/JavaScript - no frameworks or build tools required.
