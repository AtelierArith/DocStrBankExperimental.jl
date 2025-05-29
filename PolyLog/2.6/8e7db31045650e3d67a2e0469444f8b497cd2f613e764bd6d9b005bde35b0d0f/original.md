```
li(n::Integer, z::Complex)
```

Returns the complex n-th order polylogarithm $\operatorname{Li}_n(z)$ of a complex number $z$ of type `Complex` for all integers $n$.

The implementation for $n < 0$ is an adaptation of [[arxiv:2010.09860](https://arxiv.org/abs/2010.09860)].

If only real arguments $z\in\mathbb{R}$ are considered and one is interested only in the real part of the polylogarithm, $\Re[\operatorname{Li}_n(z)]$, refer to the function [`reli`](@ref), which may be a faster alternative.

See also [`reli`](@ref).

Author: Alexander Voigt

License: MIT

# Example

```jldoctest; setup = :(using PolyLog)
julia> li(10, 1.0 + 1.0im)
0.9999619510320734 + 1.0019864330842578im

julia> li(10, BigFloat("1.0") + 1im)
0.9999619510320737590142881353792522311832737465811100255090656306086896548837863 + 1.001986433084258078428884002632749111102285607210811280673320176236792560588471im
```
