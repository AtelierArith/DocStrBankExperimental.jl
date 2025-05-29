```julia
SussmanBathe(data; interpolant, k)

```

Model:

  * See paper

Parameters:

  * None

Fields:

  * `data`: Hyperelastic Uniaxial test to be used for determining the interpolation
  * `k`: Order of the summation in the model.
  * `interpolant`: Function of the form, `f(s, λ)` which returns a function `f(λ) = s`

> Sussman T, Bathe KJ. A model of incompressible isotropic hyperelastic material behavior using spline interpolations of tension–compression test data. Communications in numerical methods in engineering. 2009 Jan;25(1):53-63.

