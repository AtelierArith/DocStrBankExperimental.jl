```
total_degree(
    F::System;
    parameters = nothing,
    gamma = cis(2π * rand()),
    tracker_options = TrackerOptions(),
    endgame_options = EndgameOptions(),
)
```

システム `F` を総次数ホモトピーを使用して解きます。これにより、パストラッカー（[`EndgameTracker`](@ref) または [`OverdeterminedTracker`](@ref)）と、開始解を計算するためのイテレータが返されます。システム `F` が `variable_groups` を宣言している場合、[^\Wam93] に従った多重同次の開始システムが構築されます。

[^Wam93]: 多重同次多項式継続のための効率的な開始システム、Wampler, C.W. Numer. Math. (1993) 66: 517. https://doi.org/10.1007/BF01385710
