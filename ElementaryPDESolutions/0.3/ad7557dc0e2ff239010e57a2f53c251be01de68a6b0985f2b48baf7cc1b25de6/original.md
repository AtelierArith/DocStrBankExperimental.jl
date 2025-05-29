```
solve_brinkman(Q::NTuple{N,Polynomial{N,T}};Re=1,α=1)
```

Compute a vector of polynomials `U` and a polynomial `P` satisfying the linearized unsteady Navier-Stokes equations, sometimes referred to as the Brinkman equations or the modified Stokes equations, `(Δ - α²)U - Re ∇P = Q` with `∇⋅U = 0`. Each component of the polynomial `Q` is required to be individually homogeneous.

The solutions are given by the expressions

```
u = (Δ + α²)(Δ - ∇∇⋅)g,

p = -1/Re (Δ² - α⁴)∇⋅g,
```

where the vector potential g satisfies

```
(Δ³ - α⁴Δ)g = Q.
```

# Examples

```jldoctest
julia> Q = (Polynomial([(2, 1) => 2 // 1]), Polynomial([(0, 2) => 4 // 1]))
(2//1x²y, 4//1y²)

julia> U, P = solve_brinkman(Q; Re=Rational(1), α=Rational(1))
((0//1y + xy + 5//24y³ - 5//8x²y, 0//1 + 4//1x + 1//2x² - 1//2y² + 5//8xy² + 11//24x³), -7//6y³ - 1//2x²y - 11//24x³y - 5//24xy³)
```
