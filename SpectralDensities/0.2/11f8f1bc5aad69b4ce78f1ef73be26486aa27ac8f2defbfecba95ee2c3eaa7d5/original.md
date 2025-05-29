```
struct PolySD <: AbstractSD
```

PolySD represents a polynomial spectral density. It is characterized by an amplitude `α` representing the strength of the coupling and the polynomial degree `n`. That is

$$
J(\omega) = \alpha\omega^n
$$

# Fields

  * `α::Float64`: The amplitude `α`, indicating the strength of the coupling.
  * `n::Int`: The polynomial degree.
