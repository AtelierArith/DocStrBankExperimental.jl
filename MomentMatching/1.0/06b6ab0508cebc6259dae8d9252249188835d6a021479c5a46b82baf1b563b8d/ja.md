```julia
marginal_fobj(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult;
    which_point,
    gridx
) -> Array{Float64, 3}

```

最適化者の周りの点で目的関数を計算します。

# 必要な引数

  * estset: EstimationSetupのインスタンス。別のドキュメント[`EstimationSetup`](@ref)を参照してください。
  * mmsolu: EstimationResultのインスタンス。別のドキュメント[`EstimationResult`](@ref)を参照してください。

# オプションの引数

  * gridx: 目的関数を評価する最適点の周りの点のグリッド。
