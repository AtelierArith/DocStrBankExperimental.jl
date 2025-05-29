```
syz = syzygies(G)
```

Return all relations between the elements of G.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R = @ring! ℤ[x,y];

julia> I = [x^5, x^2 + y, x*y + y^2];

julia> G, tr = gröbner_transformation(I);

julia> K = syzygies(G) * tr; # the kernel of the map R^3 -> I induced by these generators

julia> iszero(K * I)
true
```
