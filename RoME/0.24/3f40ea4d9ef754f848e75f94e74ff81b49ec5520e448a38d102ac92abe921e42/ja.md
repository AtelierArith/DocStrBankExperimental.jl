```julia
generateGraph_ZeroPose(
;
    varType,
    graphinit,
    solverParams,
    dfg,
    doRef,
    useMsgLikelihoods,
    label,
    priorType,
    μ0,
    Σ0,
    priorArgs,
    solvable,
    variableTags,
    factorTags,
    postpose_cb
)

```

Pose2 `:x0` と共分散 `P0` を持つ MvNormal を用いて、標準的な因子グラフを生成します。

ノート

  * 例えば `varType=Point2` を使用して、デフォルトの変数タイプ `Pose2` から変更します。
  * `priorArgs::Tuple` を使用して、`priorType` へのデフォルト入力引数を上書きします。
  * コールバック `postpose_cb(g::AbstractDFG,lastpose::Symbol)` を使用して、各ポーズステップの後にユーザー操作を呼び出します。
