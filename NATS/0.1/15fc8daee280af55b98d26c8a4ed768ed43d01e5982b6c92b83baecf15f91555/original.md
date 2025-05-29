```julia
next(connection, sub, batch; no_wait, no_throw)

```

Obtains batch of messages for synchronous subscription.

Optional keyword arguments:

  * `no_wait`: do not wait for next message, return empty vector if buffer is empty
  * `no_throw`: do not throw exception, stops collecting messages on error
