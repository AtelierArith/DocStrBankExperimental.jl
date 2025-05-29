```
getSignal(signalTable, name::String)
```

信号 `name` を `signalTable` から返します（それは [`Var`](@ref)、[`Par`](@ref) または [`Map`](@ref) です）。`name` が存在しない場合、エラーが発生します。
