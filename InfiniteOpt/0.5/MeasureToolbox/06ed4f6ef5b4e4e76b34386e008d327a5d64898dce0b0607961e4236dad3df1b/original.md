```
integral(expr::JuMP.AbstractJuMPScalar,
         prefs::AbstractArray{GeneralVariableRef},
         [lower_bounds::Union{Real, AbstractArray{<:Real}} = [lower_bound(pref)...],
         upper_bounds::Union{Real, AbstractArray{<:Real}} = [upper_bound(pref)...];
         kwargs...])::GeneralVariableRef
```

Returns a measure reference that evaluates the integral of `expr` with respect to infinite parameters `prefs` from `lower_bounds` to `upper_bounds`. This thus considers integrals of the form: $\int_{p \in P} expr(p) w(p) dp$ where $p$ is an infinite parameter and $w$ is the weight function is 1 by default. This function provides a high-level interface that ultimately constructs an appropriate concrete form of [`AbstractMeasureData`](@ref) via [`generate_integral_data`](@ref) in accordance with the keyword arugment `eval_method` that is then used with [`measure`](@ref). Note that it is preferred to call [`@integral`](@ref) when `expr` is not just a single variable reference. Errors when the container types and dimensions do not match or the bounds are invalid.

The keyword arguments are as follows:

  * `eval_method::AbstractMultivariateMethod`: Used to determine the   numerical evaluation scheme. Possible choices include:

      * [`Automatic()`](@ref MeasureToolbox.Automatic)
      * [`MultiMCSampling()`](@ref MeasureToolbox.MultiMCSampling)
      * [`MultiIndepMCSampling()`](@ref MeasureToolbox.MultiIndepMCSampling)
  * `num_supports`: The minimum number of supports to be generated (if used by   `eval_method`)
  * `weight_func`: $w(p)$ above with parameter value inputs and scalar output

See [`set_multi_integral_defaults`](@ref) to update the default keyword argument values for all multi-dimensional integral calls.

**Example**

```julia-repl
julia> @infinite_parameter(model, x[1:2] in [0, 1], independent = true);

julia> @variable(model, f, Infinite(x));

julia> int = integral(f, x)
∫{x ∈ [0, 1]^2}[f(x)]
```
