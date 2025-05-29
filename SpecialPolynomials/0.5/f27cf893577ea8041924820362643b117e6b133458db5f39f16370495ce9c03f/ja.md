```
DualBernstein{N, α, β, T, X}
```

内積 `<f,g> = ∫₀¹ (1-x)ᵅ xᵝ f(x) g(x) dx` とベルンシュタイン多項式 `Bᵢⁿ(x)` を考えると、双対ベルンシュタイン多項式は `<Bᵢⁿ, Dⱼⁿ(x;α,β)> = δᵢⱼ` を満たします。

## 例

```julia
julia> n,α,β = 5, 0, 0;

julia> D = DualBernstein{n,α,β}
DualBernstein{5, 0, 0}

julia> bi = basis(D, 3)
DualBernstein(1.0⋅βᵅᵝ₅,₃(x))

julia> bi(0.2)
7.910400000000036
```

`f` のベルンシュタイン-ベジェ形式は `α-β` ノルムに対する最小二乗誤差の値を最小化します。

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

## 参考

実装は [Chudy and Woźny](https://arxiv.org/abs/2004.09801) に従っています。
