```
default_stepsize(M::AbstractManifold, ams::AbstractManoptSolverState)
```

指定された [`AbstractManoptSolverState`](@ref) `ams` が `AbstractManifold M` 上で目的関数を実行する際に使用されるデフォルトの [`Stepsize`](@ref) ファンクタを返します。
