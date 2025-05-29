```
I, E = quadde(f::Function, a::Real, b::Real, c::Real...;
              atol::Real=zero(Float64),
              rtol::Real=atol>0 ? zero(Float64) : sqrt(eps(Float64)))
```

任意の区間 [a, b] で `f(x)` を数値的に積分し、積分値 `I` と推定誤差 `E` を返します。`E` は真の値との差と正確に等しいわけではありません。しかし、`E <= max(atol, rtol*norm(I))` が真であれば、積分値 `I` が収束していると期待できます。そうでない場合、得られた `I` は信頼できない可能性があり、収束する前に繰り返し回数が `maxlevel` を超えます。オプションとして、積分区間 [a, b, c...] を分割することもでき、これは `∫ f(x)dx in [a, b] + ∫f(x)dx in [b, c[1]] + ⋯` を返します。各端点は不連続性や特異性を許容することに注意が必要です。

被積分関数 `f` は、スカラー以外の任意の値を返すこともできます。`+`、`-`、実数による乗算、`LinearAlgebra.norm` が実装されている限り、問題ありません。例えば、数値の `Vector` や `Array` は受け入れ可能ですが、残念ながら、あまりパフォーマンスが良くないかもしれません。

# 例

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> f(x) = 2/(1 + x^2);

julia> I, E = quadde(f, -1, 1);

julia> I ≈ π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = quadde(x -> [1/(1 + x^2), 2/(1 + x^2)], 0, Inf);

julia> I ≈ [π/2, π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = quadde(x -> 1/sqrt(abs(x)), -1, 0, 1);  # x = 0 で特異点

julia> I ≈ 4
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
