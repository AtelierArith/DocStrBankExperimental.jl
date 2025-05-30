```julia
marginal_fobj(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult,
    num_marg::Integer,
    scale_margs::AbstractVector;
    which_point
) -> Array{Float64, 3}

```

最適化者の周りの点で目的関数を計算します。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。
  * num_marg: 評価する最適点の周りの点の数。
  * scale_margs: 評価される点のグリッドを構築するためのスケールパラメータ。
