```
get_stopping_criterion(ams::AbstractManoptSolverState)
```

[`AbstractManoptSolverState`](@ref) `ams` に格納されている [`StoppingCriterion`](@ref) を返します。

装飾されていない状態の場合、これは `ams.stop` にあると仮定されます。あなたの manopt ソルバー (`yms`) のためにこれを変更するには、`_get_stopping_criterion(yms::YMS)` を上書きしてください。`yms` は YMS 型であると仮定します。
