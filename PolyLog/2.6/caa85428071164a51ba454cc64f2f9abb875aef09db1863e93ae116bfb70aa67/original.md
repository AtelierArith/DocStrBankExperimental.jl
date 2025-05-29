```
reli2(x::Real)
```

Returns the real dilogarithm $\Re[\operatorname{Li}_2(x)]$ of a real number $x$ of type `Real`.

For $x$ of type `Float16`, `Float32` or `Float64` the implementation is an adaptation of [[arXiv:2201.01678](https://arxiv.org/abs/2201.01678)].

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> reli2(1.0)
1.6449340668482264

julia> reli2(BigFloat("1.0"))
1.644934066848226436472415166646025189218949901206798437735558229370007470403202
```
