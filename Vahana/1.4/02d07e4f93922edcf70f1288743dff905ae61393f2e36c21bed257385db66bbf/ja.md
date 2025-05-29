```
push_global!(sim::Simulation, name, value)
```

`Simulation`コンストラクタの`globals`構造体のフィールドがベクター（例：時系列データの場合）である場合、`push_global!`を使用してこのベクターに値を追加できます。これは、`set_global!(sim, name, push!(get_global(sim, name), value)`と書く代わりに使用します。

並列シミュレーションでは、すべてのプロセスで`push_global!`を呼び出す必要があり、すべてのプロセスで同一の`value`を使用する必要があります。

`push_global!`は遷移関数内で呼び出してはいけません。

他にも[`create_model`](@ref)、[`mapreduce`](@ref)、[`set_global!`](@ref)および[`get_global`](@ref)を参照してください。
