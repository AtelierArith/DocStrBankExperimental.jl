```
get_last_stepsize(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, vars...)
```

[`AbstractManoptSolverState`](@ref) `ams` 内に保存された最後に計算されたステップサイズを返します。これは [`AbstractManoptProblem`](@ref) `amp` を解く際に使用されます。

このメソッドは、`ams` が装飾されている可能性があることを考慮しています。これが `NaN` を返す場合、保存されたステップサイズへの具体的な呼び出しが行われます。このためには、通常、`vars...` の最初の要素が現在の反復値である必要があります。
