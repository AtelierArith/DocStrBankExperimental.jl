```
stepNoise()
```

Compose a discontinuous function of many square bumps and troughs, following a white noise process.     'stepHeight':   the standard deviation of the step height     'T':            a tuple, (t0, tmax)

# Examples

```julia-repl
julia> D = stepNoise();
D([-1, 0, 1])
```
