```julia
next(T, connection, sub, batch; no_wait, no_throw)

```

Obtains batch of messages for synchronous subscription converting them to reqested `T` type.

Optional keyword arguments:

  * `no_wait`: do not wait for next message, return empty vector if buffer is empty
  * `no_throw`: do not throw exception, stops collecting messages on error
