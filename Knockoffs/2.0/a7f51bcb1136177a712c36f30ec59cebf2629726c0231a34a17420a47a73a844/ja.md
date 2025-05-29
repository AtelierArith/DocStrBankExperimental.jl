```
solve_s(Σ::Symmetric, method::Symbol; m=1, kwargs...)
```

生成的ノックオフのためにベクトル `s` を解決します。`Σ` は一般的な共分散行列である必要がありますが、`Symmetric` キーワードでラップされている必要があります。

# 入力

  * `Σ`: 共分散行列（`Symmetric(Σ)` を明示的にラップする必要があります）
  * `method`: 次のいずれかである必要があります

      * `:mvr` 最小分散ベースの再構成可能性ノックオフ（参照2のアルゴリズム1）
      * `:maxent` 最大エントロピーのノックオフ（参照2のアルゴリズム2）
      * `:equi` 等距離ノックオフ（参照1の式2.3）
      * `:sdp` SDPノックオフ（参照1の式2.4）
      * `:sdp_ccd` 座標降下法による高速SDPノックオフ（参照3のアルゴリズム2.2）
  * `m`: 変数ごとのノックオフの数、デフォルトは1です。
  * `kwargs`: 特定のメソッドに利用可能な追加引数。たとえば、MVRノックオフの収束許容誤差を緩和するには、`tol = 0.001` を指定します。利用可能なオプションのリストについては、[`solve_MVR`](@ref)、[`solve_max_entropy`](@ref)、[`solve_sdp_ccd`](@ref)、[`solve_SDP`](@ref)、または [`solve_equi`](@ref) を参照してください。

# 参考文献

1. "Controlling the false discovery rate via Knockoffs" by Barber and Candes (2015).
2. "Powerful knockoffs via minimizing reconstructability" by Spector, Asher, and Lucas Janson (2020)
3. "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).
