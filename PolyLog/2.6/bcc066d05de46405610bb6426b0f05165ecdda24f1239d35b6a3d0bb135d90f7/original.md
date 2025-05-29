```
li4(z::Complex)
```

Returns the complex 4th order polylogarithm $\operatorname{Li}_4(z)$ of a complex number $z$ of type `Complex`.

If only real arguments $z\in\mathbb{R}$ are considered and one is interested only in the real part of the 4th order polylogarithm, $\Re[\operatorname{Li}_4(z)]$, refer to the function [`reli4`](@ref), which may be a faster alternative.

See also [`reli4`](@ref).

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li4(1.0 + 1.0im)
0.9593189135784194 + 1.138039196676983im
```
