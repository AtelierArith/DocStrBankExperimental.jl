```
unsubscribe_async(client::Client, topics::String...)
```

Unsubscribes the `Client` instance from the supplied topic names. Deletes the callback from the client Returns a `Future` object that contains `nothing` on success and an exception on failure.
