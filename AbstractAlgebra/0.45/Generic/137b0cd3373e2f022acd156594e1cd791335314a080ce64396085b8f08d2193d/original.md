```
hom(R::AbstractAlgebra.PolyRing, S::NCRing, [coeff_map,] image)
```

Given a homomorphism `coeff_map` from `C` to `S`, where `C` is the  coefficient ring of `R`, and given an element `image` of `S`, return the homomorphism from `R` to `S` whose restriction  to `C` is `coeff_map`, and which sends the generator of `R` to `image`.

If no coefficient map is entered, invoke a canonical homomorphism of `C` to `S`, if such a homomorphism exists, and throw an error, otherwise.

# Examples

```jldoctest
julia> Zx, x = ZZ[:x];

julia> F = hom(Zx, Zx, x + 1);

julia> F(x^2)
x^2 + 2*x + 1

julia> Fp = GF(3); Fpy, y = Fp[:y];

julia> G = hom(Zx, Fpy, c -> Fp(c), y^3);

julia> G(5*x + 1)
2*y^3 + 1
```
