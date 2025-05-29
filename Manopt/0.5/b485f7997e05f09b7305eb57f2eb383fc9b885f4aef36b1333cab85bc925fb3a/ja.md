```
dispatch_state_decorator(s::AbstractManoptSolverState)
```

内部的に、[`AbstractManoptSolverState`](@ref) `s` が装飾型であるかどうかを示し、デフォルトでフィールド `s.state` に状態を格納（カプセル化）します。

デコレーターは、さらなるディスパッチのために `Val{true}` を返すことでこれを示します。

デフォルトは `Val{false}` であり、したがってデフォルトでは状態は装飾されていません。
