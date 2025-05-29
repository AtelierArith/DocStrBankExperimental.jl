```
refine_profile!(prof::ProfileLikelihoodSolution, n;
    alg=get_optimiser(prof.likelihood_solution),
    conf_level::F=0.95,
    confidence_interval_method=:spline,
    threshold=get_chisq_threshold(conf_level),
    target_number=10,
    normalise::Bool=true,
    spline_alg=FritschCarlsonMonotonicInterpolation,
    extrap=Line,
    parallel=false,
    kwargs...) where {F}
```

既存の `prof::ProfileLikelihoodSolution` を考慮して、`n` のパラメータに対するプロファイル結果を、より多くのポイントを追加することで洗練します。キーワード引数は [`profile`](@ref) と同じです。`target_number` は最終的に含まれるべきポイントの総数です（追加されるポイントの数ではありません）。
