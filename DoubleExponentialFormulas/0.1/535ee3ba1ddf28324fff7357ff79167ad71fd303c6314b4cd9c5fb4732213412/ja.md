```
QuadSS(T::Type{<:AbstractFloat}; maxlevel::Integer=10, h0::Real=one(T)/8)
```

範囲 (-∞, ∞) で関数を統合するための呼び出し可能なオブジェクトで、*sinh-sinh quadrature* を使用します。これは、変数の変換を利用して、被積分関数を台形法に適した形に変換します。

`QuadSS` は、最大で `maxlevel` 回、積分値を計算しようとします。台形のステップサイズは `h0` から始まり、各繰り返しで半分にされ、より高い精度が得られます。繰り返しは、前の推定値との違いが特定の閾値より小さくなると終了します。この閾値は、実行時のパラメータによって決定されます。詳細は以下を参照してください。

型 `T` は区間の精度を表します。被積分関数は、`x<:T` をパラメータとして受け入れる必要があります。

---

```
I, E = (q::QuadSS)(f::Function;
                   atol::Real=zero(T),
                   rtol::Real=atol>0 ? zero(T) : sqrt(eps(T)))
                   where {T<:AbstractFloat}
```

区間 (-∞, ∞) で `f(x)` を数値的に統合し、積分値 `I` と推定誤差 `E` を返します。`E` は真の値との差と正確に等しいわけではありません。しかし、`E <= max(atol, rtol*norm(I))` が真であれば、積分値 `I` が収束していると期待できます。そうでなければ、得られた `I` は信頼できないものとなり、収束する前に繰り返しの回数が `maxlevel` を超えます。

被積分関数 `f` は、スカラー以外の任意の値を返すこともできます。`+`、`-`、実数による乗算、`LinearAlgebra.norm` が実装されている限り、受け入れられます。たとえば、数値の `Vector` や `Array` は受け入れられますが、残念ながら、あまりパフォーマンスが良くないかもしれません。

# 例

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> qss = QuadSS(Float64);

julia> f(x) = 2/(1 + x^2);

julia> I, E = qss(f);

julia> I ≈ 2π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = qss(x -> [1/(1 + x^2), 2/(1 + x^2)]);

julia> I ≈ [π, 2π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
