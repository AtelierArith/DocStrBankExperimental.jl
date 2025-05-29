```
finite_field(p::IntegerUnion, d::Int, s::VarName = :o; cached::Bool = true, check::Bool = true)
finite_field(q::IntegerUnion, s::VarName = :o; cached::Bool = true, check::Bool = true)
finite_field(f::FqPolyRingElem, s::VarName = :o; cached::Bool = true, check::Bool = true)
```

Return a tuple $(K, x)$ of a finite field $K$ of order $q = p^d$, where $p$ is a prime, and a generator $x$ of $K$ (see [`gen`](@ref) for a definition). The identifier $s$ is used to designate how the finite field generator will be printed.

If a polynomial $f \in k[X]$ over a finite field $k$ is specified, the finite field $K = k[X]/(f)$ will be constructed as a finite field with base field $k$.

See also [`GF`](@ref) which only returns $K$.

# Examples

```jldoctest
julia> K, a = finite_field(3, 2, "a")
(Finite field of degree 2 and characteristic 3, a)

julia> K, a = finite_field(9, "a")
(Finite field of degree 2 and characteristic 3, a)

julia> Kx, x = K["x"];

julia> L, b = finite_field(x^3 + x^2 + x + 2, "b")
(Finite field of degree 3 over GF(3, 2), b)
```
