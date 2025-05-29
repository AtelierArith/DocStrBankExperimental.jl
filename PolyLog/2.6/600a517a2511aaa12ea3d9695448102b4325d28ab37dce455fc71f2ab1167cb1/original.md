```
reli3(x::Real)
```

Returns the real trilogarithm $\Re[\operatorname{Li}_3(x)]$ of a real number $x$ of type `Real`.

For $x$ of type `Float16`, `Float32` or `Float64` the implementation is an adaptation of [[arXiv:2308.11619](https://arxiv.org/abs/2308.11619)].

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> reli3(1.0)
1.2020569031595942
```
