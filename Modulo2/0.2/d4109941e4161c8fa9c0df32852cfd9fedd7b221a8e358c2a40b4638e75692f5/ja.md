```
mul!(c::ZZ2Vector, a::ZZ2Matrix, b::AbstractVector{<:Number}, α::Number = ZZ2(1), β::Number = ZZ2(0)) -> c
```

結合された行列-ベクトルの乗算加算 `α a*b + β c` を `c` に格納し、`c` を返します。デフォルト値の `α` と `β` を使用すると、積 `a*b` が計算されます。`b` の要素と `α` および `β` は `ZZ2` に変換可能でなければなりません。

この関数は `LinearAlgebra` モジュールから再エクスポートされています。
