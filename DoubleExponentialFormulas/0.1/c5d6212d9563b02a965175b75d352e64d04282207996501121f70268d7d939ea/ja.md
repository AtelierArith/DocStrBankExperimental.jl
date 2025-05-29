```
quaddeo(f::Function, ω::Real, θ::Real, a::Real, b::Real;
        h0::Real=one(ω)/5, maxlevel::Integer=12,
        atol::Real=zero(ω),
        rtol::Real=atol>0 ? zero(atol) : sqrt(eps(typeof(atol))))
```

任意の区間 [a, b] で `f(x)` を数値的に積分し、積分値 `I` と推定誤差 `E` を返します。`quaddeo` 関数は減衰振動積分に特化しています。

```
f(x) = f₁(x)sin(ωx + θ),
```

ここで `f₁(x)` は減衰代数関数です。`ω` と `θ` は積分の振動部分の周波数と位相です。振動部分が `sin(ωx)` の場合、`θ = 0.0` です。代わりに `cos(ωx)` の場合は `θ = π/(2ω)` です。`E` は真の値との差と正確に等しくはありませんが、`E <= max(atol, rtol*norm(I))` が真であれば、積分値 `I` が収束していると期待できます。そうでない場合、得られた `I` は信頼できないものであり、収束する前に繰り返し回数が `maxlevel` を超えます。オプションとして、積分区間 [a, b, c...] を分割することができ、`∫ f(x)dx in [a, b] + ∫f(x)dx in [b, c[1]] + ⋯` を返します。各端点は不連続性や特異性を許容することに注意が必要です。

被積分関数 `f` は、スカラー以外の任意の値を返すこともできます。`+`、`-`、実数による乗算、`LinearAlgebra.norm` が実装されている限りです。例えば、数値の `Vector` や `Array` は受け入れられますが、残念ながら、あまりパフォーマンスが良くないかもしれません。

# 例

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> f(x) = sin(x)/x;

julia> I, E = quaddeo(f, 1.0, 0.0, 0.0, Inf);

julia> I ≈ π/2
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
