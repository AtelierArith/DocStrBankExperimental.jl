```
apply(r::ElemRestriction, u::AbstractVector; tmode=NOTRANSPOSE)
```

[`ElemRestriction`](@ref)を使用してLベクトルからEベクトルに変換します（または転置操作を適用します）。入力は`u`で、結果は`Vector{CeedScalar}`型の配列として返されます。
