```
Lagrange(xs, [ws], coeffs, [var])
```

点 `(xᵢ, fᵢ)` のラグランジュ補間 `i ∈ 0..n`。

  * `xs`, `coeffs`: 補間する座標。
  * `ws`: バリセント表現で使用される重み。(`SpecialPolynomials.lagrange_barycentric_weights` または `SpecialPolynomials.lagrange_barycentric_nodes_weights` から。)
  * var: 多項式の不確定量

# 拡張ヘルプ

点 `(xᵢ, fᵢ)` のラグランジュ補間 `i ∈ 0:n` は多項式 `p(x) = ∑ᵢ lⱼ(x) fⱼ` です。

基底ベクトル `lⱼ(x)` は `xⱼ` で `1` であり、`i ≠ j` のとき `xᵢ` で `0` です。すなわち、`lⱼ(x) = Π_{i ≠ j}(x-xᵢ)/Π_{i ≠j}(xⱼ-xᵢ)` です。これらは重み `wⱼ` の観点から書き換えることができ、`lⱼ = l(x) wⱼ/(x - xⱼ)` となり、`l(x) = Π(x-xᵢ)` です。さらに進むと、バリセント公式が得られます：

`p(x) = (∑ wⱼ / (x - xⱼ) ⋅ fⱼ) /  (∑ wⱼ / (x - xⱼ) )`。

この表現にはいくつかの特性があり、Berrut と Trefethen の [Barycentric Lagrange Interpolation](https://doi.org/10.1137/S0036144502417715) に詳述されています。

## 例

```jldoctest Lagrange
julia> using Polynomials, SpecialPolynomials

julia> p =  Lagrange([1,2,3], [1,2,3])
Lagrange(1⋅ℓ_0(x) + 2⋅ℓ_1(x) + 3⋅ℓ_2(x))

julia> p.([1,2,3]) # 係数
3-element Vector{Int64}:
 1
 2
 3

julia> convert(Polynomial,  p)
Polynomial(1.0*x)
```

インスタンスは表現に必要なノードと重みを保持しているため、型だけでは `variable` や `convert(Lagrange, ...)` のような関数には使用できません。前者にはインスタンスを使用でき、後者には `fit` を使用できます：

```jldoctest Lagrange
julia> p =  Lagrange([1,2,3], [1,2,3])
Lagrange(1⋅ℓ_0(x) + 2⋅ℓ_1(x) + 3⋅ℓ_2(x))

julia> variable(p)
Lagrange(1⋅ℓ_0(x) + 2⋅ℓ_1(x) + 3⋅ℓ_2(x))

julia> q = Polynomial([0,0,1])
Polynomial(x^2)

julia> qq = fit(Lagrange, p.xs, p.ws, q)
Lagrange(1⋅ℓ_0(x) + 4⋅ℓ_1(x) + 9⋅ℓ_2(x))

julia> convert(Polynomial, qq)
Polynomial(1.0*x^2)
```

与えられたノードのセットに対して、`SpecialPolynomials.lagrange_barycentric_weights` は重みを計算できます。`n` の値が控えめでない限り、補間多項式はノードが適切に選ばれないとランゲ現象に悩まされます。（ノードは `[-1,1]` 上で `1/√(1-x^2)` の漸近密度を持つべきです。）`P=Chebyshvev` および `P=ChebyshevU` に対して、関数 `SpecialPolynomials.lagrange_barycentric_nodes_weights(P, n)` は `[-1,1]` 上の `n+1` 点の良い選択と事前計算された重みを返します。

```jldoctest Lagrange
julia> xs, ws = SpecialPolynomials.lagrange_barycentric_nodes_weights(Chebyshev, 64);


julia> f(x) = exp(-x)*sinpi(x)
f (generic function with 1 method)

julia> p = fit(Lagrange, xs, f.(xs));


julia> degree(p)
64

julia> maximum(abs.(f(x) - p(x) for x in range(-1, 1, length=20))) <= 1e-14
true
```

!!! note
    上記の例は `fit(Chebyshev, f, 64)` を通じてより直接的に行うことができますが、結果として得られる多項式は異なる基底を参照します。


```
