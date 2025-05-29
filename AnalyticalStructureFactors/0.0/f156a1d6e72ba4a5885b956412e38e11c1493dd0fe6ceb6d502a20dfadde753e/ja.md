```
S_Yukawa_RPA(ϕ::T, amplitude::T, inv_screening_length::T) where {T<:AbstractFloat}
```

静的構造因子を計算する関数 `f(k)` を返します。これは、RPAを使用してユカワポテンシャルを持つ流体のためのものです。システムとポテンシャルのパラメータ（ϕ、振幅、逆スクリーン長）は固定されています。

# 引数

  * `ϕ::T`: 球体の体積分率。
  * `amplitude::T`: ユカワポテンシャルの有効振幅。
  * `inv_screening_length::T`: 無次元の逆スクリーン長（z）。

# 戻り値

  * `Function`: 波ベクトル `k` を受け取り、`S(k)` を返す関数。
