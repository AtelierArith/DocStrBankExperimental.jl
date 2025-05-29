```
mean_return_times(ds::DynamicalSystem, u₀, εs, T; kwargs...) → τ, c
```

状態空間の部分集合に対して平均帰還時間 `τ` と帰還の回数 `c` を返します。これらの部分集合は `u₀, εs` によって定義されます。`ds` は最大 `T` 時間進化します。

この関数は、[`exit_entry_times`](@ref) への呼び出し、その後 [`transit_return`](@ref) への呼び出し、そしていくつかの平均化を行う便利なラッパーです。したがって、`u₀` と `εs` の意味やさらなる情報については、[`exit_entry_times`](@ref) を参照してください。
