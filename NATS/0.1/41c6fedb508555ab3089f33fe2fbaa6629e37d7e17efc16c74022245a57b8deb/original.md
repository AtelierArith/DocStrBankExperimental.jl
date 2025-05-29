```julia
next(T, connection, sub; no_wait, no_throw)

```

Obtains next message for synchronous subscription converting it to requested `T` type.

Optional keyword arguments:

  * `no_wait`: do not wait for next message, return `nothing` if buffer is empty
  * `no_throw`: do not throw exception, returns `nothing` if cannot get next message
