```
DualBernstein{N, α, β, T, X}
```

Given the inner product `<f,g> = ∫₀¹ (1-x)ᵅ xᵝ f(x) g(x) dx` and the Bernstein polynomials `Bᵢⁿ(x)` the dual Bernstein polynomials satisfy `<Bᵢⁿ, Dⱼⁿ(x;α,β)> = δᵢⱼ`

## Example

```julia
julia> n,α,β = 5, 0, 0;

julia> D = DualBernstein{n,α,β}
DualBernstein{5, 0, 0}

julia> bi = basis(D, 3)
DualBernstein(1.0⋅βᵅᵝ₅,₃(x))

julia> bi(0.2)
7.910400000000036
```

The Bernstein-Bezier form of `f` minimizes the value of the least-square error for the `α-β` norm.

```julia
julia> f(x) = sinpi(x);

julia> n, α, β = 5, 1/2, 1/2
(5, 0.5, 0.5)

julia> B, D = Bernstein{n}, DualBernstein{n,α,β};

julia> Iₖ = [ip(f, basis(D,k), α, β) for k in 0:n];

julia> pₙ = B(Iₖ);

julia> λ = x -> f(x) - pₙ(x);

julia> SpecialPolynomials.innerproduct(ShiftedJacobi{α, β}, λ, λ)
0.00017514530881540565
```

## Reference

The implementation follows that of [Chudy and Woźny](https://arxiv.org/abs/2004.09801).
