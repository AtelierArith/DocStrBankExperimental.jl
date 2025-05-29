```
`SaveConfidence(sols::AbstractVector{<:AbstractODESolution}, N::Int=500; sigdigits::Int=7, adaptive::Bool=true) -> Matrix`
`SaveConfidence(Planes::AbstractVector{<:Plane}, sols::AbstractVector{<:AbstractODESolution}, N::Int=500; sigdigits::Int=7, adaptive::Bool=true) -> Matrix`

`sols`の各`ODESolution`の評価回数に対応する`N`行の`Matrix`を返します。列は評価された解のさまざまな成分に対応します。例えば、3つの成分を持つ`ODESolution`の場合、`Matrix`の4列目は`sols[2]`の評価された最初の成分に対応します。
```
