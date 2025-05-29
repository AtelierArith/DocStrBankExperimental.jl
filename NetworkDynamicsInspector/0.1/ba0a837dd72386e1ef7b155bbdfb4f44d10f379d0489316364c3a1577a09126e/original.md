```
inspect(sol; restart=false, reset=false, display=nothing)
```

Main entry point for gui. Starts the server and serves the app for soution `sol`.

  * `restart`: If `true`, the display will be restartet (i.e. new Electron window, new server or new Browser tab)
  * `reset`: If `true`, reset the appstate with the new solution `sol`.
  * `display=CURRENT_DISPLAY[]`: Can be `BrowserDisp()`, `ServerDisp()` or `ElectronDisp()`.  Per default, the current display will be used (defaults to`BrowserDisp()`).
