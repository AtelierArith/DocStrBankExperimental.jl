```
modify_global!(sim::Simulation, name, f)
```

シミュレーション `sim` の `globals` 構造体の `name` フィールドの値を、現在の値を引数として受け取る `f` 関数を使用して変更します。

これは [`set_global!`](@ref) と [`get_global`](@ref) の組み合わせです: `set_global!(sim, name, f(get_global(sim, name)))`。

`modify_global!` は遷移関数内で呼び出してはいけません。

並列シミュレーションでは、すべてのプロセスで `push_global!` を呼び出し、すべてのプロセスで同一の `value` を使用する必要があります。

さらに [`create_simulation`](@ref)、[`mapreduce`](@ref)、[`set_global!`](@ref)、[`push_global!`](@ref) および [`get_global`](@ref) を参照してください。
