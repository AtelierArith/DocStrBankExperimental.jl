```
invariant_sets!(sets, modes_to_compute, system::AbstractHybridSystem,
                args...; kwargs...)
```

`invariant_sets(system, args...; kwargs...)`と似ていますが、結果を`sets`に格納し、`modes_to_compute`で指定されたモードのみを計算します。`modes_to_compute`に含まれない`enabled`の他のセットは、`sets`に指定された値を持つと仮定されます。
