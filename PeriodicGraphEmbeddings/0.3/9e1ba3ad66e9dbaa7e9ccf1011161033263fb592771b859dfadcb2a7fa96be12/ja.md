```
PeriodicDistance2(mat::AbstractMatrix{T}) where T
```

[`PeriodicDistance2`](@ref) オブジェクトを構築し、与えられた行列 `mat` の単位セル内で平方周期距離を計算するために呼び出すことができます。

!!! warning
    `mat` の `eltype` `T` は `isbitstype` でなければならず、そうでない場合は構築に失敗します。必要に応じて入力を適切な型に変換してください。


!!! warning
    単位セルは標準設定にあると仮定されます：その角度は60°以上でなければならず、そうでない場合は返される距離が最短でない可能性があります。

