```
S_SALR_RPA(ϕ::T, amplitude_attr::T, inv_screening_length_attr::T, amplitude_rep::T, inv_screening_length_rep::T) where {T<:AbstractFloat}
```

静的構造因子を計算する関数 `f(k)` を返します。これは、RPAを使用してSALRポテンシャルを持つ流体のためのものです。システムとSALRポテンシャルのパラメータは固定されています。

# 引数

  * `ϕ::T`: 球体の体積分率。
  * `amplitude_attr::T`: ユカワの引力成分の振幅。
  * `inv_screening_length_attr::T`: 引力成分の逆遮蔽長。
  * `amplitude_rep::T`: ユカワの反発成分の振幅。
  * `inv_screening_length_rep::T`: 反発成分の逆遮蔽長。

# 戻り値

  * `Function`: 波ベクトル `k` を受け取り、`S(k)` を返す関数。
