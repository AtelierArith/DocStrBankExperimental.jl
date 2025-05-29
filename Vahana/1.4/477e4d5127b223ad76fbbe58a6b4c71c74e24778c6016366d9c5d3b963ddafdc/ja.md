```
set_global!(sim::Simulation, name, value)
```

シミュレーション `sim` の `globals` 構造体のフィールド `name` の値を設定します。

並列シミュレーションでは、`set_global!` はすべてのプロセスで呼び出され、すべてのプロセスで同一の `value` でなければなりません。

`set_global!` は遷移関数内で呼び出してはいけません。

他にも [`create_simulation`](@ref)、[`mapreduce`](@ref)、[`modify_global!`](@ref)、[`push_global!`](@ref)、および [`get_global`](@ref) を参照してください。
