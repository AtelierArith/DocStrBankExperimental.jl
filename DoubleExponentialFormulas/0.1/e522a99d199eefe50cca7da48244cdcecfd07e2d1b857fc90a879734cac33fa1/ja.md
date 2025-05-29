```
QuadES(T::Type{<:AbstractFloat}; maxlevel::Integer=10, h0::Real=one(T)/8)
```

関数を範囲 [0, ∞) で *exp-sinh quadrature* を使用して統合するための呼び出し可能なオブジェクトです。これは、変数の変換を利用して被積分関数を台形法に適した形に変換します。

`QuadES` は、最大で `maxlevel` 回、積分値を計算しようとします。台形のステップサイズは `h0` から始まり、各繰り返しで半分にされ、より高い精度が得られます。前の推定値との差が特定の閾値より小さくなると、繰り返しは終了します。閾値は実行時パラメータによって決定されます。以下を参照してください。

型 `T` は区間の精度を表します。被積分関数は、`x<:T` をパラメータとして受け入れる必要があります。

---

```
I, E = (q::QuadES)(f::Function;
                   atol::Real=zero(T),
                   rtol::Real=atol>0 ? zero(T) : sqrt(eps(T)))
                   where {T<:AbstractFloat}
```

区間 [0, ∞) で `f(x)` を数値的に統合し、積分値 `I` と推定誤差 `E` を返します。`E` は真の値との差と正確には等しくありません。しかし、`E <= max(atol, rtol*norm(I))` が真であれば、積分値 `I` が収束していると期待できます。そうでなければ、得られた `I` は信頼できないものであり、収束する前に繰り返しの回数が `maxlevel` を超えます。

被積分関数 `f` は、スカラー以外の任意の値を返すこともできます。`+`、`-`、実数による乗算、`LinearAlgebra.norm` が実装されている限り、受け入れられます。たとえば、数値の `Vector` や `Array` は受け入れられますが、残念ながら、あまりパフォーマンスが良くないかもしれません。

# 例

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> qes = QuadES(Float64);

julia> f(x) = 2/(1 + x^2);

julia> I, E = qes(f);

julia> I ≈ π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = qes(x -> [1/(1 + x^2), 2/(1 + x^2)]);

julia> I ≈ [π/2, π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
