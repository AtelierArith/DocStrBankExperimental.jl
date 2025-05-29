```
li1(z::Complex)
```

Returns the complex 1st order polylogarithm $\operatorname{Li}_1(z) = -\ln(1 - z)$ of a complex number $z$ of type `Complex`.

If only real arguments $z\in\mathbb{R}$ are considered and one is interested only in the real part, $\Re[\operatorname{Li}_1(z)]$, refer to the function [`reli1`](@ref), which may be a faster alternative.

See also [`reli1`](@ref).

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li1(1.0 + 1.0im)
-0.0 + 1.5707963267948966im

julia> li1(BigFloat("1.0") + 1im)
-0.0 + 1.570796326794896619231321691639751442098584699687552910487472296153908203143099im
```
