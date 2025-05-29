```
fixed_knockoffs(X::Matrix{T}; [method], [kwargs...])
```

固定Xノックオフを作成します。内部的に、`X`はノックオフを計算する前に自動的に正規化されます。

# 入力

  * `X`: 列正規化された `n × p` 数値行列で、各行はサンプル、各列は共変量です。内部的に、`X`が正規化されていない場合は正規化されます。
  * `method`: 次のいずれかの値を取ることができます

      * `:mvr`: 最小分散ベースの再構成可能性ノックオフ（参照2のアルゴリズム1）
      * `:maxent`: 最大エントロピーのノックオフ（参照2のアルゴリズム2）
      * `:equi`: 等距離ノックオフ（参照1の式2.3）
      * `:sdp`: SDPノックオフ（参照1の式2.4）
      * `:sdp_fast`: 座標降下法によるSDPノックオフ（参照3のアルゴリズム2.2）
  * `kwargs...`: `method`への可能なオプション入力、[`solve_MVR`](@ref)、[`solve_max_entropy`](@ref)、および[`solve_sdp_ccd`](@ref)を参照してください。

# 出力

  * `GaussianKnockoff`: 元の（列正規化された）`X`とそのノックオフ`X̃`、および他の変数（例：`s`）を含む構造体です。

# 参考文献

1. "Controlling the false discovery rate via Knockoffs" by Barber and Candes (2015).
2. "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020)
3. "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).
