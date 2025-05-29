```
S_Yukawa_RPA(ϕ::T, amplitude::T, inv_screening_length::T, k::T) where {T<:AbstractFloat}
```

Yukawaポテンシャルを持つ流体の静的構造因子をランダム位相近似（RPA）を用いて計算します。基準系はVerlet-Weiss補正を持つ硬球です。

RPAの一般的な式は次のとおりです： S(k) = 1 / ( 1/S₀(k) - ρ*factor * β * u*pert*tilde(k) ) ここで、S₀(k)は基準系の構造因子、ρ*factorは密度に関連する因子（通常はσ=1のとき6ϕ/π）、u*pert*tilde(k)はポテンシャルの摂動部分のフーリエ変換です。

# 引数

  * `ϕ::T`: 球体の体積分率。
  * `amplitude::T`: Yukawaポテンシャルの有効振幅（通常はβを含む、例：βε）。
  * `inv_screening_length::T`: 無次元逆スクリーン長（z）。
  * `k::T`: 無次元波ベクトル（k = qσ）。

# 戻り値

  * `T`: 構造因子S(k)の値。
