```
onjs(session::Session, obs::Observable, func::JSCode)
```

Register a javascript function with `session`, that get's called when `obs` gets a new value. If the observable gets updated from the JS side, the calling of `func` will be triggered entirely in javascript, without any communication with the Julia `session`.
