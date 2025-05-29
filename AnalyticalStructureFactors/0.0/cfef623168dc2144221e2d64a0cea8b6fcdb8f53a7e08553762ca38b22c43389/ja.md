```
S_Yukawa_RPA(ϕ::T, amplitude::T, inv_screening_length::T, k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

kの値のベクトルに対する構造因子S(k)を計算します。

# 引数

  * `ϕ::T`: 体積分率。
  * `amplitude::T`: ユカワポテンシャルの振幅。
  * `inv_screening_length::T`: 逆スクリーン長。
  * `k_values::AbstractVector{T}`: 無次元のk値のベクトル。

# 戻り値

  * `Vector{T}`: `k_values`の各kに対応するS(k)の値のベクトル。
