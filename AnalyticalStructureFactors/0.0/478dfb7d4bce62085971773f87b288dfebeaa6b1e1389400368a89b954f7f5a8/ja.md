```
S_SALR_RPA(ϕ::T, amplitude_attr::T, inv_screening_length_attr::T, amplitude_rep::T, inv_screening_length_rep::T, k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

SALRポテンシャルに対するk値のベクトルのための構造因子S(k)を計算します。

# 引数

  * `ϕ::T`: 体積分率。
  * `amplitude_attr::T`: ユカワの引力成分の振幅。
  * `inv_screening_length_attr::T`: 引力成分の逆スクリーン長。
  * `amplitude_rep::T`: ユカワの斥力成分の振幅。
  * `inv_screening_length_rep::T`: 斥力成分の逆スクリーン長。
  * `k_values::AbstractVector{T}`: 無次元のk値のベクトル。

# 戻り値

  * `Vector{T}`: `k_values`の各kに対応するS(k)の値のベクトル。
