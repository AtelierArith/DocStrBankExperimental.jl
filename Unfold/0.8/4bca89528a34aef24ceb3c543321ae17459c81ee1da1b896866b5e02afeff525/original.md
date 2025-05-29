```julia
firbasis(τ, sfreq; ...)
firbasis(τ, sfreq, name; interpolate, scale_duration)

```

Generate a sparse FIR basis around the *τ* timevector at sampling rate *sfreq*. This is useful if you cannot make any assumptions on the shape of the event responses. If unrounded events are supplied, they are split between samples. E.g. event-latency = 1.2 will result in a "0.8" and a "0.2" entry.

Advanced: second input can be duration in samples - careful: `times(firbasis)` always assumes duration = 1. Therefore, issues with LMM and predict will appear!

# keyword arguments

`interpolate` (Bool, default false): if true, interpolates events between samples linearly. This results in `predict` functions to return a trailling 0``scale_duration`(Union{Bool,Interpolations-Interpolator}, default false):     if true, scales the response by the fit-kwargs`eventfields`second entry. That is, the FIR becomes a stepfunction instead of a impulse response.     if Interpolations.interpolator, e.g.`Interpolations.Linear()`- uses the fit-kwargs`eventfields`second entry to stretch the FIR kernel based on`imresize`. This implements Hassall

# Examples

Generate a FIR basis function from -0.1s to 0.3s at 100Hz

```julia-repl
julia>  f = firbasis([-0.1,0.3],100)
```

Evaluate at an event occuring at sample 103.3

```julia-repl
julia>  f(103.3)
```
