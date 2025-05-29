```
QuadDE(T::Type{<:AbstractFloat}; maxlevel::Integer=10, h0::Real=one(T)/8)
```

任意の区間で関数を積分するための呼び出し可能なオブジェクトで、*二重指数公式*、または*tanh-sinh 量子化*およびその変種を使用します。これは、変数の変換を利用して、被積分関数を台形法に適した形に変換します。

`QuadDE`は、最大で`maxlevel`回積分値を計算しようとします。台形のステップサイズは`h0`から始まり、より細かい精度のために各繰り返しで半分にされます。繰り返しは、前回の推定値との差が特定の閾値より小さくなると終了します。この閾値は実行時のパラメータによって決定されます。詳細は以下を参照してください。

型`T`は区間の精度を表します。被積分関数は、`x<:T`をそのパラメータとして受け入れる必要があります。

---

```
I, E = (q::QuadDE{T})(f::Function, a::Real, b::Real, c::Real...;
                      atol::Real=zero(T),
                      rtol::Real=atol>0 ? zero(T) : sqrt(eps(T)))
                      where {T<:AbstractFloat}
```

任意の区間[a, b]で`f(x)`を数値的に積分し、積分値`I`と推定誤差`E`を返します。`E`は真の値との差と正確に等しいわけではありません。しかし、`E <= max(atol, rtol*norm(I))`が真であれば、積分値`I`が収束していると期待できます。そうでなければ、得られた`I`は信頼できないものとなります; 収束する前に繰り返しの回数が`maxlevel`を超えます。オプションとして、積分区間[a, b, c...]を分割することもでき、`∫f(x)dx in [a, b] + ∫f(x)dx in [b, c[1]] + ⋯`を返します。各端点は不連続性や特異点を許可することに注意が必要です。

被積分関数`f`は、スカラー以外の任意の値を返すこともできます。`+`、`-`、実数による乗算、`LinearAlgebra.norm`が実装されている限りです。例えば、`Vector`や`Array`の数値は受け入れられますが、残念ながら、あまりパフォーマンスが良くないかもしれません。

# 例

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> qde = QuadDE(Float64);

julia> f(x) = 2/(1 + x^2);

julia> I, E = qde(f, -1, 1);

julia> I ≈ π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> g(x) = [1/(1 + x^2), 2/(1 + x^2)];

julia> I, E = qde(g, 0, Inf);

julia> I ≈ [π/2, π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> h(x) = 1/sqrt(abs(x));  # x = 0での特異点

julia> I, E = qde(h, -1, 0, 1);

julia> I ≈ 4
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
