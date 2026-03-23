# 🚀 Share Buttons Library

A collection of modern, lightweight, and fast share buttons for social networks and messaging apps. The buttons are built in a modular way using pure HTML, CSS, and Vanilla JavaScript, without external libraries (no jQuery), with a strong focus on performance, accessibility (a11y), and SEO.

## ✨ Key Features & Benefits

- **Vanilla JS (No jQuery):** Lightweight, fast load times, and modern code using `addEventListener`.
- **Separation of Concerns:** The HTML is completely clean of `onclick` attributes or PHP snippets. Logic is strictly separated into JS, and styling into CSS.
- **SEO & Security Optimized:** All external links are equipped with `rel="nofollow noopener noreferrer"` tags by default.
- **Full Accessibility (a11y):** Support for keyboard navigation (`:focus-visible`), `aria-label` tags for screen readers, and hiding graphical SVG elements from assistive technologies (`aria-hidden="true"`, `focusable="false"`).
- **Smart Dynamic Links:** The sharing scripts automatically detect the current page URL (`window.location.href`), but also support passing specific links via the `data-url` attribute – perfect for use inside loops (like blog posts or product grids).
- **Safe Link Copying:** Uses the modern `navigator.clipboard` API with a reliable fallback for older browsers.

## 📦 Supported Networks & Actions

- Facebook
- Twitter / X
- Pinterest
- WhatsApp (Share link, send direct message, multiple designs)
- LinkedIn
- Houzz
- Telegram
- Email (mailto)
- Facebook Messenger
- Navigation (Waze)
- Copy URL to clipboard
- Print Page

## 🛠️ Usage Instructions

Each button in the library consists of up to 3 components that can be copied separately from the dashboard:

1. **HTML:** Paste the HTML code exactly where you want the button to appear on your site.
2. **CSS:** Copy the CSS (if applicable) to your site's main stylesheet. *Note: Some buttons use inline styling for maximum convenience and portability.*
3. **JavaScript:** Copy the JS code to your site's script file. It is highly recommended to wrap the code inside a `DOMContentLoaded` event listener to ensure the DOM is fully loaded before the script runs.

### Using Data Attributes

The JS is built flexibly, allowing you to control the shared data directly from the HTML without needing to modify the JavaScript code.

* `data-url="..."`: The link you want to share. If left empty or omitted, the JS will automatically fall back to the current page's URL.
    * *Example for PHP/WordPress:* `data-url="<?php echo esc_url(get_permalink()); ?>"`
* `data-title="..."`: The page title (relevant for LinkedIn and Houzz).
* `data-img="..."`: The image path/URL (relevant for Pinterest and Houzz).
* `data-description="..."`: A short description (relevant for Pinterest).

### Basic Button Structure Example (Facebook):

```html
<button type="button" class="facebook-share-btn" data-url="[https://example.com](https://example.com)" aria-label="Share on Facebook" title="Share on Facebook">
    </button>

<script>
document.querySelectorAll('.facebook-share-btn').forEach(function(btn) {
    btn.addEventListener('click', function(e) {
        e.preventDefault();
        var url = this.getAttribute('data-url') || window.location.href;
        window.open('[https://www.facebook.com/sharer/sharer.php?u=](https://www.facebook.com/sharer/sharer.php?u=)' + encodeURIComponent(url), '', 'width=900,height=300');
    });
});
</script>
