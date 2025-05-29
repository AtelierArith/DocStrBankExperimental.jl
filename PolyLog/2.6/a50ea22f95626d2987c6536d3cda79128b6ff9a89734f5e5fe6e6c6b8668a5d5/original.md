```
li2(z::Complex)
```

Returns the complex dilogarithm $\operatorname{Li}_2(z)$ of a complex number $z$ of type `Complex`.

If only real arguments $z\in\mathbb{R}$ are considered and one is interested only in the real part of the dilogarithm, $\Re[\operatorname{Li}_2(z)]$, refer to the function [`reli2`](@ref), which may be a faster alternative.

See also [`reli2`](@ref).

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li2(1.0 + 1.0im)
0.6168502750680851 + 1.4603621167531196im

julia> li2(BigFloat(1) + 1im)
0.6168502750680849136771556874922594459571062129525494141508343360137528014012052 + 1.460362116753119547679775739491787597608795299373993707847946932920340157070418im
```
