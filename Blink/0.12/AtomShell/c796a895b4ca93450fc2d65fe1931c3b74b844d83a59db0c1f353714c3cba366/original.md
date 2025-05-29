```
Window()
Window(electron_options::Dict; async=true)
```

Create and open a new Window through Electron.

If `async==false`, this function blocks until the Window is fully initialized and ready for you to communicate with it via javascript or the Blink API.

The `electron_options` dict is used to initialize the Electron window. See here for the full set of Electron options: https://electronjs.org/docs/api/browser-window#new-browserwindowoptions
