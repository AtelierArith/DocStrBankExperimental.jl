```
heideldiag(
    x::AbstractVector{<:Real}; alpha::Real=0.05, eps::Real=0.1, start::Int=1, kwargs...
)
```

Compute the Heidelberger and Welch diagnostic [^Heidelberger1983]. This diagnostic tests for non-convergence (non-stationarity) and whether ratios of estimation interval halfwidths to means are within a target ratio. Stationarity is rejected (0) for significant test p-values. Halfwidth tests are rejected (0) if observed ratios are greater than the target, as is the case for `s2` and `beta[1]`.

`kwargs` are forwarded to [`mcse`](@ref).

[^Heidelberger1983]: Heidelberger, P., & Welch, P. D. (1983). Simulation run length control in the presence of an initial transient. Operations Research, 31(6), 1109-1144.
