```
SaveGeodesics(sols::AbstractVector{<:AbstractODESolution}, N::Int=500; sigdigits::Int=7, adaptive::Bool=true) -> Matrix
```

`sols`の各`ODESolution`の評価回数に対応する`N`行の`Matrix`を返します。列は評価された解のさまざまな成分に対応します。測地線の解オブジェクトは成分の後半に速度を含むため、成分の前半のみが保存されます。
