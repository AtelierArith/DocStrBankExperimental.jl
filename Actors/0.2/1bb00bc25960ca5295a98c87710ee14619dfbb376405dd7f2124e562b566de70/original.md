```
Bhv(func, a...; kw...)(c...)
```

A callable struct to represent actor behavior. It is executed with parameters from the incoming communication.

# Parameters

  * `f`: a callable object,
  * `a...`: stored acquaintance parameters to `f`,
  * `kw...`: stored keyword arguments,
  * `c...`: parameters from the incoming communication.
