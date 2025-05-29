```
halfdegree(t::AbstractTermLike)
```

Return the equivalent of `ceil(degree(t)/2)``for real-valued terms or`degree_complex(t)`for terms with only complex variables; however, respect any mixing between complex and real-valued variables. To be well-defined, the monomial must not contain real parts or imaginary parts of variables. If`x₁`and`x₂`are real-valued variables and`z₁`and`z₂` are complex-valued,

  * `halfdegree(x₁^2 * x₂^3) = ⌈5/2⌉ = 3`
  * `halfdegree(z₁^3 * conj(z₁)^4) = max(3, 4) = 4` and `halfdegree(z₁^4 * conj(z₁)^3) = max(4, 3) = 4`
  * `halfdegree(z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = max(4, 6) = 6` and `halfdegree(z₁^4 * z₂ * conj(z₁) * conj(z₂)^3) = max(5, 4) = 5`
  * `halfdegree(x₁^2 * x₂^3 * z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = ⌈5/2⌉ + max(4, 6) = 9`
