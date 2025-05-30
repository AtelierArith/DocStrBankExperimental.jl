```
UnravelledLayout
```

Parameters are

  * `x` (a function to get the value on x)
  * `y` (a function to get the value on y)

Both of these functions *must* accept a unipartite network as input, and return a dictionary with species and a single numerical value as output. Note that `x` and/or `y` can be `λ`s.
