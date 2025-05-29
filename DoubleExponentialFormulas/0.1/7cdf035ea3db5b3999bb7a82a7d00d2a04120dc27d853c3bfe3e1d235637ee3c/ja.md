```
QuadTS(T::Type{<:AbstractFloat}; maxlevel::Integer=10, h0::Real=one(T)/8)
```

範囲[-1, 1]で関数を積分するための呼び出し可能なオブジェクトで、*tanh-sinh quadrature*を使用します。変数の変換を利用して、被積分関数を台形法に適した形に変換します。

`QuadTS`は、最大で`maxlevel`回積分値を計算しようとします。台形のステップサイズは`h0`から始まり、より高い精度のために各繰り返しで半分にされます。前の推定値との差が特定の閾値より小さくなると繰り返しは終了します。閾値は実行時パラメータによって決定されます。以下を参照してください。

型`T`は区間の精度を表します。被積分関数は、`x<:T`をそのパラメータとして受け入れる必要があります。

---

```
I, E = (q::QuadTS)(f::Function;
                   atol::Real=zero(T),
                   rtol::Real=atol>0 ? zero(T) : sqrt(eps(T)))
                   where {T<:AbstractFloat}
```

区間[-1, 1]で`f(x)`を数値的に積分し、積分値`I`と推定誤差`E`を返します。`E`は真の値との差と正確に等しいわけではありません。しかし、`E <= max(atol, rtol*norm(I))`が真であれば、積分値`I`が収束していると期待できます。そうでなければ、得られた`I`は信頼できないものとなり、収束する前に繰り返しの回数が`maxlevel`を超えます。

被積分関数`f`は、スカラー以外の任意の値を返すこともできます。`+`、`-`、実数による乗算、`LinearAlgebra.norm`が実装されている限りです。例えば、数値の`Vector`や`Array`は受け入れ可能ですが、残念ながら、あまりパフォーマンスが良くないかもしれません。

# 例

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> qts = QuadTS(Float64);

julia> f(x) = 2/(1 + x^2);

julia> I, E = qts(f);

julia> I ≈ π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = qts(x -> [1/(1 + x^2), 2/(1 + x^2)]);

julia> I ≈ [π/2, π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
