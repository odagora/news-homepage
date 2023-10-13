# Frontend Mentor - News homepage solution

This is a solution to the [News homepage challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/news-homepage-H6SWTa1MFl). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

**Note: Delete this note and update the table of contents based on what sections you keep.**

## Overview

### The challenge

Users should be able to:

- View the optimal layout for the interface depending on their device's screen size
- See hover and focus states for all interactive elements on the page

### Screenshot

![Mobile Version](https://bit.ly/3PTMHAi)
![Desktop Version](https://bit.ly/45yaPhz)

### Links

- Solution URL: [click here](https://github.com/odagora/news-homepage)
- Live Site URL: [click here](https://odagora.github.io/news-homepage/)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- CSS transitions
- Mobile-first workflow

### What I learned

1. Use of CSS Grid responsive design under a `div` container:
    ```html
    <div class="container">
      <header></header>
      <main></main>
      <aside></aside>
      <section></section>
    </div>
    ```
    ```css
    .container {
      margin: 0 auto;
      width: min(90%, 1200px);
      position: relative;
      display: grid;
    }
    ```
2. Use of `grid-template-areas` for the layout:
    ```css
    .posts-container article {
      display: grid;
      grid-template-columns: 1fr 2fr;
      grid-template-areas:
        "image title"
        "image subtitle"
        "image text"
      ;
      margin-bottom: 2.5em;
    }

    .posts-container figure {
      grid-area: image;
      margin-right: 1.6em;
    }

    .posts-container h2 {
      grid-area: title;
      font-size: 3.5em;
      margin-bottom: 0.1em;
      color: var(--neutral-text-color-02);
    }

    .posts-container h3 {
      grid-area: subtitle;
      margin-bottom: 0.7em;
      font-size: 1.8em;
      font-weight: 800;
    }
    ```
  3. Use of CSS transitions for menu drawer animation:
      ```css
      /* For the main menu drawer */
      .nav {
        position: fixed;
        padding: 15em 2em;
        width: 70%;
        top: 0;
        right: 0;
        height: 100vh;
        background-color: white;
        z-index: 1;
        transform: translateX(100%);
        transition: transform 0.5s ease-in-out;
      }

      .nav.visible {
        transform: translateX(0);
      }
      /* For the open/close icon */
      .nav-icon span {
        position: absolute;
        width: 100%;
        height: 3px;
        background-color: black;
        opacity: 1;
        left: 0;
        transform: rotate(0deg);
        transition: 0.25s ease-in-out;
        transform-origin: left center;
        -moz-transform: rotate(0deg);
        -o-transform: rotate(0deg);
        -webkit-transform: rotate(0deg);
        -webkit-transition: 0.25s ease-in-out;
        -webkit-transform-origin: left center;
        -moz-transform-origin: left center;
        -o-transform-origin: left center;
      }

      .nav-icon span:nth-child(1) {
        top: 0;
      }

      .nav-icon.open span:nth-child(1) {
        top: 0px;
        left: 8px;
        transform: rotate(45deg);
        -webkit-transform: rotate(45deg);
        -moz-transform: rotate(45deg);
        -o-transform: rotate(45deg);
      }

      .nav-icon span:nth-child(2) {
        top: 9px;
      }

      .nav-icon.open span:nth-child(2) {
        width: 0;
        opacity: 0;
      }

      .nav-icon span:nth-child(3) {
        top: 18px;
      }

      .nav-icon.open span:nth-child(3) {
        top: 35px;
        left: 8px;
        transform: rotate(-45deg);
        -webkit-transform: rotate(-45deg);
        -moz-transform: rotate(-45deg);
        -o-transform: rotate(-45deg);
      }
      ```
  4. Use of an overlay when menu drawer is visible:
      ```html
      <!-- Overlay as the main container-->
      <div class="overlay">
        <nav class="nav">
          <ul class="nav__list">
            <li class="nav__item">
              <a href="#" class="nav__link">Home</a>
            </li>
            <li class="nav__item">
              <a href="#" class="nav__link">New</a>
            </li>
            <li class="nav__item">
              <a href="" class="nav__link">Popular</a>
            </li>
            <li class="nav__item">
              <a href="" class="nav__link">Trending</a>
            </li>
            <li class="nav__item">
              <a href="" class="nav__link">Categories</a>
            </li>
          </ul>
        </nav>
      </div>
      ```
      ```css
      .overlay.visible {
        position: fixed;
        height: 100vh;
        width: 100%;
        top: 0;
        right: 0;
        transition: 0.3s linear;
        background-color: rgba(0, 0, 0, 0.5);
      }
      ```
  5. Use of JavaScript `classList.toggle` to switch CSS classes with ease:
      ```js
      const overlay = document.querySelector(".overlay");
      const navMenu = document.querySelector(".nav");
      const navIcon = document.querySelector(".nav-icon");

      function toggleMenu() {
        navMenu.classList.toggle("visible");
        overlay.classList.toggle("visible");
        navIcon.classList.toggle("open");
      }

      navIcon.addEventListener("click", toggleMenu);
      ```

### Continued development

- Use of preprocessors like SASS for styling
- Use of CSS Grid in complex layouts
- Use of transformations and animations with CSS
- Implementation of UI testing
- Use of accessibility principles
- Cross-browser support
- Use of web components for reusability

### Useful resources

- [A complete guide to CSS Grid](https://css-tricks.com/snippets/css/complete-guide-grid/) - This helped me for the site layout. I really liked this pattern and will use it going forward whenever I come across complex designs.
- [An interactive guide to CSS transitions](https://www.joshwcomeau.com/animation/css-transitions/) - This is an amazing interactive website that helped me understand the transitions and animations concepts. I'd recommend it to anyone still learning this concept.

## Author

- Website - [Daniel González](https://odagora.com)
- Frontend Mentor - [@odagora](https://www.frontendmentor.io/profile/odagora)
- Twitter - [@odagora](https://www.twitter.com/odagora)

## Acknowledgments

The Frontend Platzi courses helped me out with the basic concepts of semantic HTML, CSS3, transitions and animations.
