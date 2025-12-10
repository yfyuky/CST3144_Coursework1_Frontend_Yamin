# CST3144_Coursework1_Frontend_Yamin# My Frontend for CST3144 Coursework

**Name:** Yamin Rizwan
**ID:** M00913254  
**Module:** CST3144 Full Stack Development

---

## What is this?

This is my after-school lessons booking website. Students can look at lessons, add them to a cart, and book them.

You can see it here: https://yfyuky.github.io/CST3144_Coursework1_Frontend_Yamin/

---

## What I used

- Vue.js - makes the page reactive (updates automatically)
- HTML - the structure
- CSS - to make it look nice
- JavaScript - for all the logic
- Font Awesome - for the icons

---

## How to run it

1. Download the files (index.html, app.js, styles.css)
2. Open with VS Code
3. Right click index.html
4. Click "Open with Live Server"

Or just visit the GitHub Pages link above.

---

## What you can do

**See lessons** - 12 different lessons show up when you open the page

**Sort** - You can sort by subject, location, price, or how many spaces are left. And choose if you want it ascending or descending.

**Add to cart** - Click the blue button to add a lesson to your cart. The button goes gray if there's no spaces left.

**View cart** - Click the cart icon at the top to see what you added.

**Remove from cart** - If you change your mind, click remove on any lesson.

**Search** - Type anything in the search box and it filters the lessons. It searches the title, location, and description.

**Checkout** - Fill in your name (only letters) and phone (only numbers). The checkout button only works if you filled it in correctly. When you checkout, it saves your order to the database.

---

## How it works

1. When you open the page, it fetches all lessons from my backend
2. Vue.js displays them as cards
3. When you click "Add to Cart", it adds it to an array
4. When you checkout, it sends your info to the backend
5. The backend saves it to MongoDB
6. Then it updates how many spaces are left

---

## The tricky bits I had to do

**Sorting** - I made a computed property that sorts the lessons array based on what you picked. It can go forwards or backwards.

**Form validation** - I used regex to check the name only has letters and phone only has numbers. The checkout button is disabled until both are valid.

```javascript
// Name validation
/^[A-Za-z\s]+$/.test(this.checkout.name)

// Phone validation
/^[0-9]+$/.test(this.checkout.phone)
```

**Search** - The search sends a request to my backend with the search term. The backend searches the database and sends back only the matching lessons. Then Vue displays those.

**Cart** - I had to make sure when you remove something from cart, it adds the spaces back to that lesson. And when you add something, it takes spaces away.

---

## Connecting to the backend

The frontend talks to the backend at this URL:
```
https://cst3144-coursework1-backend-yamin.onrender.com
```

I use fetch() to send requests:

```javascript
// Get lessons
fetch('https://backend-url/lessons')

// Make order
fetch('https://backend-url/orders', {
  method: 'POST',
  body: JSON.stringify(orderData)
})

// Update spaces
fetch('https://backend-url/lessons/2001', {
  method: 'PUT',
  body: JSON.stringify({ availableSeats: 4 })
})

// Search
fetch('https://backend-url/search?q=math')
```

---

## Problems I had

**Problem 1:** The lessons weren't showing up  
I forgot to put `await` when fetching from the backend. Once I added async/await it worked.

**Problem 2:** CORS errors  
My backend wasn't allowing requests from GitHub Pages. I had to tell my backend to allow my GitHub Pages URL in the CORS settings.

**Problem 3:** Cart getting messed up  
Sometimes the available spaces would go negative. I fixed it by checking if spaces > 0 before allowing someone to add to cart.

**Problem 4:** Checkout button always enabled  
I had to make it only enable when BOTH name and phone are valid. I used a computed property that checks both validations.

---

## What I learned

- How Vue.js works (data binding, computed properties, methods)
- Using fetch to get data from APIs
- Form validation with regex
- Sorting arrays in JavaScript
- CSS flexbox for layout
- Deploying to GitHub Pages

---

## File structure

```
index.html - the main page
app.js - all the Vue.js code
styles.css - all the styling
```

Pretty simple, everything in just 3 files!

---

## Coursework requirements I did

-  Display lessons using v-for
-  Sort by 4 things (subject, location, price, spaces)
-  Can choose ascending or descending
-  Add to cart button that disables when no spaces
-  Shopping cart page
-  Remove from cart
-  Checkout form with validation
-  Search that works with the backend

---

## Testing

I tested by:
- Opening the site and trying everything
- Adding lessons to cart
- Removing them
- Trying to checkout with invalid info
- Searching for different things
- Checking the browser console for errors

---

## If I had more time

I would add:
- A favorites list
- User login so people can see their past orders
- Better mobile design
- Animations when adding to cart
- Star ratings you can click on

---

That's it! Pretty straightforward. If you want to see it, just go to the GitHub Pages link at the top.

**Last updated:** December 2025