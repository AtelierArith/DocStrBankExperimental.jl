```
BandedSylvesterRecurrence{T, TA<:AbstractMatrix{T}, TB<:AbstractMatrix{T}, TC<:AbstractMatrix{T}, TX<:AbstractMatrix{T}} <: AbstractLinearRecurrence{slicetype(TX)}
```

無限シルベスター方程式 $AX+XB+C=0$ から生成される再帰で、$X$ が無限の列を持つと仮定します。$A$ の上部バンド幅は有限でなければならず、$B$ の下部バンド幅は正で有限でなければならず、$B$ の下部境界バンドにはゼロを含むことができません。この再帰は基本的に十字型のステンシル再帰であり、ステンシルの幅は $B$ の総バンド幅によって決まり、高さは $A$ のそれによって決まります。 [`BandedSylvesterRecurrencePlan`](@ref) も参照してください。

!!! note
    バンド幅に対する制限は最適ではないかもしれませんが、現時点での私たちの知識の境界です。


# 特性

  * `A::TA, B::TB, C::TC`: 行列 $A$, $B$ および $C$。パフォーマンスを向上させるために `BandedMatrices.jl` の使用を推奨します。これらの次元は一致する必要はありません。再帰中に `BoundsError` が発生しないことを確認してください。
  * `buffer::TX`: 一時的な結果を格納するバッファ。
  * `sliceind::Int`: 現在の列インデックス。
  * `lastind::Int`: 計算される最後の列インデックス。
