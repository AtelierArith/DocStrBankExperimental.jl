```
check_vector_transport(
    M::AbstractManifold,
    vector_transport_method::AbstractVectorTransportMethod,
    p=rand(M),
    X=rand(M; vector_at=p),
    Y=rand(M; vector_at=p);
    #
    exactness_tol::Real = 1e-12,
    io::Union{IO,Nothing} = nothing,
    limits::Tuple = (-8.0, 0.0),
    log_range::AbstractVector = range(limits[1], limits[2]; length=N),
    N::Int = 101,
    name::String = "inverse retraction",
    plot::Bool = false,
    second_order::Bool = true
    slope_tol::Real = 0.1,
    error::Symbol = :none,
    window = nothing,
)
```

Check numerically wether the retraction `vector_transport_to` is correct, by selecting a set of points $q_i = \exp_p (t_i X)$ where $t$ takes all values from `log_range`, to then compare [`parallel_transport_to`](@ref) to the `vector_transport_method` applied to the vector `Y`.

This requires the [`exp`](@ref), [`parallel_transport_to`](@ref) and [`norm`](@ref) function to be implemented for the [`AbstractManifold`](@ref) `M`.

This implements a method similar to [Boumal:2023; Section 4.8 or Section 6.8](@cite).

Note that if the errors are below the given tolerance and the method is exact, no plot is generated,

# Keyword arguments

  * `exactness_tol`:     if all errors are below this tolerance, the differential is considered to be exact
  * `io`:                provide an `IO` to print the result to
  * `limits`:            specify the limits in the `log_range`, that is the exponent for the range
  * `log_range`:         specify the range of points (in log scale) to sample the differential line
  * `N`:                 number of points to verify within the `log_range` default range $[10^{-8},10^{0}]$
  * `name`:              name to display in the plot
  * `plot`:              whether to plot the result (if `Plots.jl` is loaded). The plot is in log-log-scale. This is returned and can then also be saved.
  * `second_order`:      check whether the retraction is of second order. if set to `false`, first order is checked.
  * `slope_tol`:         tolerance for the slope (global) of the approximation
  * `error`:             specify how to report errors: `:none`, `:info`, `:warn`, or `:error` are available
  * `window`:            specify window sizes within the `log_range` that are used for the slope estimation. the default is, to use all window sizes `2:N`.
