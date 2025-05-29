```julia
generateGraph_Beehive!(; ...)
generateGraph_Beehive!(
    poseCountTarget;
    graphinit,
    dfg,
    useMsgLikelihoods,
    solvable,
    refKey,
    addLandmarks,
    landmarkSolvable,
    poseRegex,
    pose0,
    yaw0,
    μ0,
    postpose_cb,
    locality,
    atol
)

```

蜂が巣の中を歩いていると想像してください。各ステップ（ポーズ）は、想像上のハニカム格子の1つのエッジに従い、各ステップの後に新しい方向（左または右）が確率的に選ばれ、そのプロセスが繰り返されます。

ノート

  * キーワード `locality=1` は正の `::Real` ∈ [0,∞) 値であり、数値が大きいほど、複数のステップにわたって方向の決定がより粘着性を持つことを示します。
  * キーワードコールバック関数 `postpose_cb = (fg, lastpose) -> ...` を使用して、各新しいポーズステップの直後に独自の機能をフックインします。

開発ノート

  * TODO 再帰的なジェネレーター関数として書き直す。

参照: [`generateGraph_Honeycomb!`](@ref), [`generateGraph_Hexagonal`](@ref), [`generateGraph_ZeroPose`](@ref)
