```
simulate!(grids, output_config::OutputConfig; constants = nothing, external_states = (),)
simulate!(grids, sim_config, output_config::OutputConfig; constants = nothing, external_states = (),)
```

`simulate!` はシミュレーションへの主要なエントリーポイントです。

`simulate!` は `grids` と `external_states` を前方に進化させ、`output_config` によって指定された出力を書き込みます。

# 引数

`grids::AbstractGrids` は座標系とスカラー場 `ψ` を含みます。

`sim_config::UltraDark.Config` はシミュレーションの実行方法に対するさらなる制御を提供します。

`output_config::OutputConfig` は何が出力され、いつ出力されるかを制御します。

`constants::Any` は進化の他の関数をオーバーロードするために使用でき、例えば自己相互作用を導入するために使用されます。

`external_states::Tuple{Any}` はオーバーロードと組み合わせて、シミュレーションに他の動的オブジェクトを追加するために使用できます。
