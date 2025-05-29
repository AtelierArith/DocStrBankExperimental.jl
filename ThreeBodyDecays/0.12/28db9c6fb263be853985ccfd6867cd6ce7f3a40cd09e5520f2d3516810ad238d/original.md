```
projection_integrand(function_σs, ms, σk; k)
```

Calculate the projection integrand for a given function `function_σs`, mass tuple `ms`, and Mandelstam variable `σk`, with `k` specified by a keyword argument. It returns an integrand function of x, x ∈ [0,1] to pass to a numerical integrator.

# Arguments

  * `function_σs`: A function that takes a MandelstamTuple and returns a scalar.
  * `ms`: A scalar representing the mass.
  * `σk`: A scalar representing the Mandelstam variable.
  * `k`: A scalar representing the momentum transfer (optional).

# Usage

```julia
plot(4.2, 4.6) do e1
	I = Base.Fix1(unpolarized_intensity, model)
	integrand = projection_integrand(I, masses(model), e1^2; k = 3)
	e1 * quadgk(integrand, 0, 1)[1]
end
```
