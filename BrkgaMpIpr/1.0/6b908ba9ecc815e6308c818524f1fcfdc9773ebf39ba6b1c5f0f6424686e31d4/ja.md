```
mutable struct ExternalControlParams
```

この構造体は、このフレームワークの外部で使用できる追加の制御パラメータを表します。これらのパラメータは、[`load_configuration`](@ref) と [`build_brkga`](@ref) を使用して構成ファイルから読み込むことができ、[`write_configuration`](@ref) を使用して書き込むことができます。

## フィールド

  * `exchange_interval`: エリート染色体が交換される間隔（0は交換なし）[> 0]。
  * `num_exchange_indivuduals`: 各集団から交換されるエリート染色体の数 [> 0]。
  * `reset_interval`: 集団がリセットされる間隔（0はリセットなし）[> 0]。
