```
get_record(s::AbstractManoptSolverState, [,symbol=:Iteration])
get_record(s::RecordSolverState, [,symbol=:Iteration])
```

は、`s` 内の [`RecordSolverState`](@ref) から、`Symbol symbol` に関して記録された値を `Array` として返します。デフォルトは `:Iteration` 中の任意の記録を指します。

任意の [`AbstractManoptSolverState`](@ref) で呼び出されると、このメソッドは [`RecordSolverState`](@ref) デコレーターを探し、デコレーター上で `get_record` を呼び出します。
