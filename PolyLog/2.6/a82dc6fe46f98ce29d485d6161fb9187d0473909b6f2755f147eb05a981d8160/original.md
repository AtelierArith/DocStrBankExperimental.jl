```
reli(n::Integer, x::Real)
```

Returns the real n-th order polylogarithm $\Re[\operatorname{Li}_n(x)]$ of a real number $x$ of type `Real` for all integers $n$.

The implementation for $n < 0$ is an adaptation of [[arxiv:2010.09860](https://arxiv.org/abs/2010.09860)].

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> reli(10, 1.0)
1.0009945751278182

julia> reli(10, BigFloat("1.0"))
1.000994575127818085337145958900319017006019531564477517257788994636291465151908
```
