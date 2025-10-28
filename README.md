# MWAD_EX05_image-carousel-in-react
## Date: 14/10/2025

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
### ImageCarousel.jsx
```
import React, { useState, useEffect } from "react";
import "./ImageCarousel.css";

function ImageCarousel() {
  const images = [
    "https://picsum.photos/id/1018/600/300",
    "https://picsum.photos/id/1015/600/300",
    "https://picsum.photos/id/1016/600/300",
    "https://picsum.photos/id/1020/600/300",
  ];

  const [currentIndex, setCurrentIndex] = useState(0);
  const nextImage = () => {
    setCurrentIndex((prevIndex) => (prevIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex(
      (prevIndex) => (prevIndex - 1 + images.length) % images.length
    );
  };
  useEffect(() => {
    const interval = setInterval(nextImage, 3000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="carousel-container">
      <h2>🖼️ Sanjay's React Image Carousel</h2>
      <div className="carousel">
        <button onClick={prevImage} className="nav-button">
          ⟨
        </button>
        <img
          src={images[currentIndex]}
          alt="carousel"
          className="carousel-image"
        />
        <button onClick={nextImage} className="nav-button">
          ⟩
        </button>
      </div>
      <p className="image-info">
        Image {currentIndex + 1} of {images.length}
      </p>
    </div>
  );
}

export default ImageCarousel;

```
### ImageCarousel.css
```
.fullscreen-center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;        
  width: 100vw;        
  background-color: #f5f7fa; 
  overflow: hidden;
  margin: 0;
  padding: 0;
}

.carousel-container {
  text-align: center;
  font-family: Arial, sans-serif;
  background-color: #ffffff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.25);
}

.carousel {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 15px;
}

.carousel-image {
  width: 600px;
  height: 300px;
  border-radius: 10px;
  margin: 0 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  transition: opacity 0.5s ease-in-out;
}

.nav-button {
  font-size: 24px;
  padding: 10px 15px;
  cursor: pointer;
  background-color: white;
  border: 1px solid #ccc;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}

.nav-button:hover {
  background-color: #e9ecef;
}

.image-info {
  color: gray;
  margin-top: 10px;
}

```
### App.jsx
```
import ImageCarousel from "./ImageCarousel";

function App() {
  return (
    <div>
      <ImageCarousel />
    </div>
  );
}

export default App;
```
## OUTPUT
<img width="964" height="625" alt="image" src="https://github.com/user-attachments/assets/994b80ec-1915-4d04-9953-e000dd588b47" />
<img width="951" height="610" alt="image" src="https://github.com/user-attachments/assets/d1a17095-aa60-48e2-9117-36a79eadc8a7" />
<img width="959" height="617" alt="image" src="https://github.com/user-attachments/assets/cd7a3a7c-bc0d-4b2e-b946-9261994c196d" />
<img width="957" height="615" alt="image" src="https://github.com/user-attachments/assets/5563b679-5763-48d1-989e-aebe201bcc4b" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
