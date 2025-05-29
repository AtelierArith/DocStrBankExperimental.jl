```julia
generateGraph_TwoPoseOdo(
;
    solverParams,
    varType,
    solvable,
    doRef,
    postpose_cb,
    dfg,
    addlandmark,
    fg,
    graphinit
)

```

基本的なファクターグラフをPose2で構築します。2つの`Pose2`と1つのランドマーク`Point2`変数、さらに`:x0`に対する`PriorPose2`と`:x1`に対する`Pose2Pose2`を含みます。また、ランドマーク`:l1`に対する`Pose2Point2BearingRange`も含まれます。

DevNotes

  * TODO 最新のジェネレーターAPIパターンに標準化する

参照: [`buildGraphChain!`](@ref)
