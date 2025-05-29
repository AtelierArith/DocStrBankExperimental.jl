```
simplex!(m::Minuit, strategy=1)
```

Run Simplex minimization.

## Parameters

  * `m::Minuit` : The Minuit object to minimize.
  * `strategy::Int` : The minimization strategy. The default value is 1, which is   the recommended value for most cases. The value 0 is faster, but less   reliable. The value 2 is slower, but more reliable. The value 3 or higher is slower,   but even more reliable.
