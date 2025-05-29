```julia
solveCliqUp!(fg, tree, cliqid; ...)
solveCliqUp!(fg, tree, cliqid, solveKey; ...)
solveCliqUp!(
    fg,
    tree,
    cliqid,
    solveKey,
    beliefMessages;
    verbose,
    recordcliq
)

```

ベイツリー内の1つのクリークに対して、`opt::SolverParams`に従って上向きの推論を実行します。

例

```julia
tree = buildTreeReset!(fg)
hist, upMessageOut = solveCliqUp!(fg, tree, 2)
```

注意

  * 新しい値でfgを修正します
  * 提供されていない場合、fgから上向きメッセージを計算します

開発ノート

  * isfixedlagのテスト
  * recordcliqのテスト

関連 [`solveTree!`](@ref), [`buildTreeReset!`](@ref), [`printCliqHistorySummary`](@ref), [`repeatCSMStep!`](@ref), `sandboxStateMachineStep`
