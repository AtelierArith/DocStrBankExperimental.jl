```
Space{D<:Domain, R}
```

Abstract supertype of various spaces in which a `Fun` may be defined, where `R` represents the type of the basis functions over the domain. Space maps the `Domain` to the type `R`.

For example, we have

  * `Chebyshev{Interval{Float64}} <: Space{Interval{Float64},Float64}`
  * `Laurent{PeriodicSegment{Float64}} <: Space{PeriodicSegment{Float64},ComplexF64}`
  * `Fourier{Circle{ComplexF64}} <: Space{Circle{ComplexF64},Float64}`

!!! note
    For now, `Space` doesn't contain any information about the coefficients

