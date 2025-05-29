```
d2c(sys::AbstractStateSpace{<:Discrete}, method::Symbol = :zoh; w_prewarp=0)
```

Convert discrete-time system to a continuous time system, assuming that the discrete-time system was discretized using `method`. Available methods are `:zoh, :fwdeuler´.

  * `w_prewarp`: Frequency for pre-warping when using the Tustin method, has no effect for other methods.

See also [`d2c_exact`](@ref).
