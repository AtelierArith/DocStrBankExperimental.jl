```
GF(p::IntegerUnion, d::Int, s::VarName = :o; cached::Bool = true, check::Bool = true)
GF(q::IntegerUnion, s::VarName = :o; cached::Bool = true, check::Bool = true)
GF(f::FqPolyRingElem, s::VarName = :o; cached::Bool = true, check::Bool = true)
```

Return a finite field $K$ of order $q = p^d$, where $p$ is a prime. The identifier $s$ is used to designate how the finite field generator will be printed.

If a polynomial $f \in k[X]$ over a finite field $k$ is specified, the finite field $K = k[X]/(f)$ will be constructed as a finite field with base field $k$.

See also [`finite_field`](@ref) which additionally returns a finite field generator of $K$.

# Examples

```jldoctest
julia> K = GF(3, 2, "a")
Finite field of degree 2 and characteristic 3

julia> K = GF(9, "a")
Finite field of degree 2 and characteristic 3

julia> Kx, x = K["x"];

julia> L = GF(x^3 + x^2 + x + 2, "b")
Finite field of degree 3 over GF(3, 2)
```
