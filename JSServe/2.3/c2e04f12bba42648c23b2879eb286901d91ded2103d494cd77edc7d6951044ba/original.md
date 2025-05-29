```
evaljs_value(session::Session, js::JSCode)
```

Evals `js` code and returns the jsonified value. Blocks until value is returned. May block indefinitely, when called with a session that doesn't have a connection to the browser.
