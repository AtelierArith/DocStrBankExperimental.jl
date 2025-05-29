```
unitStep(threshold::Real=0.0, baseline::Real=0.0, stepHeight::Real=1.0, stepOpt::Real=1.0)
```

Construct a constant function of 'x' that undergoes a step of size 'stepHeight' from a 'baseline' at 'threshold'. 'stepOpt' sets the value at 0. A Discontinuous type is returned, which can be called like a normal function but also contains the x-value for which there is a discontinuity.

# Examples

```julia-repl
julia> D = unitStep();
D([-1, 0, 1])
```
