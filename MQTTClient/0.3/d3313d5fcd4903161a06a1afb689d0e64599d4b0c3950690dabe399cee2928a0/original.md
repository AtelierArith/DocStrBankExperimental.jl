```
unsubscribe(client::Client, topics::String...)
```

Unsubscribes the `Client` instance from the supplied topic names. Waits until the unsubscribe is fully acknowledged. Returns `nothing` on success and an exception on failure.
