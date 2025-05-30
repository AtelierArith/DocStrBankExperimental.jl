```julia
save_estimation_lightweight(
    estset::MomentMatching.EstimationSetup,
    mmsolu::MomentMatching.EstimationResult;
    filename_suffix,
    filename,
    bestN
)

```

必要な要素を保存し、メモリを節約するための軽量版。
