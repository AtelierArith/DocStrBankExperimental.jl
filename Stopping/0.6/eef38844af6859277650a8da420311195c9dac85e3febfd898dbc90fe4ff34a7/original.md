Type: `GenericState`

Methods: `update!`, `reinit!`

A generic State to describe the state of a problem at a point x.

Tracked data include:

  * x             : current iterate
  * d [opt]       : search direction
  * res [opt]     : residual
  * current_time  : time
  * current_score : score

Constructors:     `GenericState(:: T, :: S; d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64 = NaN) where {S, T <:AbstractVector}`

```
`GenericState(:: T; d :: T = _init_field(T), res :: T = _init_field(T), current_time :: Float64 = NaN, current_score :: Union{T,eltype(T)} = _init_field(eltype(T))) where T <:AbstractVector`
```

Note: 

  * By default, unknown entries are set using `_init_field`.
  * By default the type of `current_score` is `eltype(x)` and cannot be changed once the State is created.  To have a vectorized `current_score` of length n, try something like `GenericState(x, Array{eltype(x),1}(undef, n))`.

Examples:   `GenericState(x)`   `GenericState(x, Array{eltype(x),1}(undef, length(x)))`   `GenericState(x, current_time = 1.0)`      `GenericState(x, current_score = 1.0)`

See also: `Stopping`, `NLPAtX`
