```
li3(z::Complex)
```

Returns the complex trilogarithm $\operatorname{Li}_3(z)$ of a complex number $z$ of type `Complex`.

If only real arguments $z\in\mathbb{R}$ are considered and one is interested only in the real part of the trilogarithm, $\Re[\operatorname{Li}_3(z)]$, refer to the function [`reli3`](@ref), which may be a faster alternative.

See also [`reli3`](@ref).

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li3(1.0 + 1.0im)
0.8711588834109381 + 1.267083441888924im
```
