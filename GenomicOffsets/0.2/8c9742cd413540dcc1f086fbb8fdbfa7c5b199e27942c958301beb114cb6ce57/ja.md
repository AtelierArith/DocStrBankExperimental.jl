```
fit(::Type{RDAGO}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}) where {T1<:Real,T2<:Real}
```

RDAモデルを適合させます（すなわち、冗長性分析を適用します）データ`Y`と`X`を使用して。

# 引数

  * `Y::AbstractMatrix{T1}`: 個体の遺伝子型またはアレル頻度を持つNxL行列。
  * `X::AbstractMatrix{T}`: 環境データを持つNxP行列。
  * オプションの引数:

      * `K::Int=size(Y,2)`: 保持する主要な正準軸の数。最終的な軸の数はKまたはpratioによって決まります。
      * `pratio::Float64=0.99`: 主成分サブスペースで保存される分散の比率。

# 戻り値

  * RDAGOモデル。
