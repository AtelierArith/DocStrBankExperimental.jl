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

  * estset: EstimationSetupのインスタンス。別のドキュメントを参照してください [`EstimationSetup`](@ref)。
  * mmsolu: EstimationResultのインスタンス。別のドキュメントを参照してください [`EstimationResult`](@ref)。

# オプションの引数

  * gridx: 目的関数を評価する最適解の周りの点のグリッド。
