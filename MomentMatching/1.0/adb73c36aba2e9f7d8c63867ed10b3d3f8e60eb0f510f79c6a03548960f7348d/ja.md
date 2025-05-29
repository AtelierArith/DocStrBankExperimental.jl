```julia
defaultxgrid(
    x::Vector{Float64};
    num_marg,
    scale_margs
) -> Matrix{Float64}

```

最適化者の周りの点で目的関数を計算します。

# 必要な引数

  * x: パラメータ推定値の配列。
  * num_marg: 評価する最適点の周りの点の数。
  * scale_margs: 評価される点のグリッドを構築するためのスケールパラメータ。
