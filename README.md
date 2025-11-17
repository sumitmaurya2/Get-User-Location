# 📍 Geolocation Finder App (JavaScript)

This project is a simple and interactive **Geolocation Finder App** built with **HTML, CSS, and JavaScript**.  
It uses the **Browser Geolocation API** to fetch the user's current latitude and longitude, then converts the coordinates into a human-readable address using the **OpenStreetMap Nominatim Reverse Geocoding API**.

---

## 🚀 Features

### 📌 **1. Get User Location**
- Uses `navigator.geolocation.getCurrentPosition()`
- Fetches latitude & longitude

### 🔄 **2. Reverse Geocoding**
- Sends coordinates to OpenStreetMap's Nominatim API  
- Returns readable address (city + country)

### ⚠️ **3. Error Handling Included**
Handles all major geolocation errors:
- Permission denied  
- Position unavailable  
- Request timeout  

### 🖥️ **4. Clean UI**
- A button to get location  
- A section to display the address  

---

## 🧠 Concepts Used

- Geolocation API  
- Async/Await  
- Fetch API  
- REST API consumption  
- Error handling  
- DOM manipulation  

---

## 🧩 Code Example

```javascript
navigator.geolocation.getCurrentPosition(showLocation, checkError);

const showLocation = async (position) => {
  const lat = position.coords.latitude;
  const lon = position.coords.longitude;

  const response = await fetch(
    `https://nominatim.openstreetmap.org/reverse?lat=${lat}&lon=${lon}&format=json`,
    {
      headers: {
        "Accept": "application/json",
        "User-Agent": "my-location-app/1.0 (your-email@example.com)"
      }
    }
  );

  const data = await response.json();
  locationDiv.innerText = `${data.address.city || data.address.town || data.address.village}, ${data.address.country}`;
};
