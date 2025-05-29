```julia
TrackerVJP <: VJPChoice
```

Uses Tracker.jl to compute the vector-Jacobian products. If `f` is in-place, then it uses a array of structs formulation to do scalarized reverse mode, while if `f` is out-of-place then it uses an array-based reverse mode.

Not as efficient as `ReverseDiffVJP`, but supports GPUs when doing array-based reverse mode.

## Constructor

```julia
TrackerVJP(; allow_nothing = false)
```

Keyword arguments:

  * `allow_nothing`: whether non-tracked values should be implicitly converted to zeros. In Tracker, the derivative of a function with respect to `p` which does not use `p` in any possible calculation is given an untracked return instead of zero. By default, this `nothing` Trackedness is caught in order to throw an informative error message about a potentially unintentional misdefined function. However, if this was intentional, setting `allow_nothing=true` will remove the error message.
