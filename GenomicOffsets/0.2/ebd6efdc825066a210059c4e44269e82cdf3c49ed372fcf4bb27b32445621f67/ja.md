```
fit(::Type{RONA}, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}) where {T1<:Real,T2<:Real}
```

RONAモデルをフィットさせます（すなわち、最小二乗問題を解きます）データ`Y`と`X`を使用して。

# 引数

  * `Y::AbstractMatrix{T1}`: 個体の遺伝子型またはアレル頻度を持つNxL行列。
  * `X::AbstractMatrix{T}`: 環境データを持つNxP行列。

# 戻り値

  * RONAモデル。
