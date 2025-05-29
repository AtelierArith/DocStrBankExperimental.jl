```
integral(expr::JuMP.AbstractJuMPScalar,
         pref::GeneralVariableRef,
         [lower_bound::Real = lower_bound(pref),
         upper_bound::Real = upper_bound(pref);
         kwargs...])::GeneralVariableRef
```

Returns a measure reference that evaluates the integral of `expr` with respect to infinite parameter `pref` from `lower_bound` to `upper_bound`. This thus considers integrals of the form: $\int_{p \in P} expr(p) w(p) dp$ where $p$ is an infinite parameter and $w$ is the weight function is 1 by default. This function provides a high-level interface that ultimately constructs an appropriate concrete form of [`AbstractMeasureData`](@ref) via [`generate_integral_data`](@ref) in accordance with the keyword arugment `eval_method` that is then used with [`measure`](@ref). Note that it is preferred to call [`@integral`](@ref) when `expr` is not just a single variable reference. Errors for bad bound input.

The keyword arguments are as follows:

  * `eval_method::AbstractUnivariateMethod`: Used to determine the   numerical evaluation scheme. Possible choices include:

      * [`Automatic()`](@ref MeasureToolbox.Automatic)
      * [`UniTrapezoid()`](@ref MeasureToolbox.UniTrapezoid)
      * [`UniMCSampling()`](@ref MeasureToolbox.UniMCSampling)
      * [`UniIndepMCSampling()`](@ref MeasureToolbox.UniIndepMCSampling)
      * [`Quadrature()`](@ref MeasureToolbox.Quadrature)
      * [`GaussHermite()`](@ref MeasureToolbox.GaussHermite)
      * [`GaussLegendre()`](@ref MeasureToolbox.GaussLegendre)
      * [`FEGaussLobatto()`](@ref MeasureToolbox.FEGaussLobatto)
      * [`GaussLageurre()`](@ref MeasureToolbox.GaussLaguerre)
      * [`GaussLobatto()`](@ref MeasureToolbox.GaussLobatto)
      * [`GaussChebyshev(order)`](@ref MeasureToolbox.GaussChebyshev)
      * [`GaussRadau()`](@ref MeasureToolbox.GaussRadau)
      * [`GaussJacobi(α, β)`](@ref MeasureToolbox.GaussJacobi)
  * `num_supports`: The minimum number of supports to be generated (if used by   `eval_method`)
  * `weight_func`: $w(p)$ above with parameter value inputs and scalar output

See [`set_uni_integral_defaults`](@ref) to update the default keyword argument values for all one-dimensional integral calls.

**Example**

```julia-repl
julia> @infinite_parameter(model, x in [0, 1])
x

julia> @variable(model, f, Infinite(x))
f(x)

julia> int = integral(f, x)
∫{x ∈ [0, 1]}[f(x)]

julia> expand(int)
0.2 f(0.8236475079774124) + 0.2 f(0.9103565379264364) + 0.2 f(0.16456579813368521) + 0.2 f(0.17732884646626457) + 0.2 f(0.278880109331201)
```
