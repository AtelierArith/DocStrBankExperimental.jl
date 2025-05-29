```
get_stepsize(amp::AbstractManoptProblem, ams::AbstractManoptSolverState, vars...)
```

[`AbstractManoptSolverState`](@ref) `ams` に格納されているステップサイズを返します。これは [`AbstractManoptProblem`](@ref) `amp` を解くときに使用されます。このメソッドは、デコレートされたオプションや、デフォルトで `ams.stepsize` に格納されているオプション内の [`Stepsize`](@ref) 関数にも適用されます。
