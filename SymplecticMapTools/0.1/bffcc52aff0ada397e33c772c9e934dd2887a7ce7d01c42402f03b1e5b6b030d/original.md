```
FourierCircle <: InvariantCircle
```

Constructors:

  * `FourierCircle(Na::Integer; a::AbstractArray=[], τ::Number=0., p::Integer=1)`

Fourier invariant circle data structure (see InvariantCircle), used to compute a circle z that is invariant of a map Fᵖ(z), where p is the period. This is done by storing all of the circles Fⁱ(z) for 0<=i<p. The circles are stored as Fourier series, i.e.    z(θ) = a₀ + ∑₁ᴺᵃ Aⱼ [cos(jθ), sin(jθ)]ᵀ The coefficients of the invariant circle can be accessed and set in chunks via array indexing. That is,   You can get and set a₀ of the ith circle using `z[0, i]`   You can get and set Aⱼ of the ith circle using `z[j, i]`
