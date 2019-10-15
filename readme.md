# MutationObserver

Wrapper that makes MutationObserver more easy to use.

## usage

Include the script in the page

```html
<script type="module" src="/node_modules/mutation-observer/mutation-observer.js"></script>
```

then on one of your element

```javascript
const elementToWatch = document.getElementById('myElement')
const observer = MutationObserver.observe(elementToWatch, (mutations, element) => {
  console.log(`myElement changed`)
})
```

### disconnecting
```javascript
observer.disconnect()
```

### subtree

By default the observer only watches the children of the element.  
To watch the subtree pass `true` to the 3rd argument :

```javascript
MutationObserver.observe(
  elementToWatch,
  (mut, el) => { /* callback */ },
  true
)
```

### child_list & character_data

By default the observer only responds when nodes are added or removed.  
If you want to watch for textual changes only provide the type as the 2nd argument :

```javascript
/* character data */
MutationObserver.observe(elementToWatch, MutationObserver.CHARACTER_DATA, callback)
// same as
MutationObserver.observe(elementToWatch, 'character_data', callback)
// same as
MutationObserver.observe(elementToWatch, 2, callback)

/* child list (default) */
MutationObserver.observe(elementToWatch, MutationObserver.CHILD_LIST, callback)
// same as
MutationObserver.observe(elementToWatch, 'child_list', callback)
// same as
MutationObserver.observe(elementToWatch, 1, callback)
// same as
MutationObserver.observe(elementToWatch, callback) // default
```

## Installation

```npm i mutation-observer```