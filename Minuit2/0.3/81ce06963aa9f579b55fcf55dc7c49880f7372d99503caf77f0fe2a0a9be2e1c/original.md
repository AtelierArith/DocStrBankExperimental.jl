```
scan!(m::Minuit, maxfcn = 0, strategy=1)
```

Run Scan algorithm to find the minimum. Thus is a brute force algorithm that scans the function in a hypercube around the initial values. The values must be within the limits.

## Arguments

  * `m::Minuit` : The Minuit object to minimize.
  * `maxfcn::Int=0` : Maximum number of function calls. If set to 0, Minuit will use a default value.
  * `strategy::Int=1` : The minimization strategy. The default value is 1, which is   the recommended value for most cases. The value 0 is faster, but less   reliable. The value 2 is slower, but more reliable. The value 3 or higher is slower,   but even more reliable.
