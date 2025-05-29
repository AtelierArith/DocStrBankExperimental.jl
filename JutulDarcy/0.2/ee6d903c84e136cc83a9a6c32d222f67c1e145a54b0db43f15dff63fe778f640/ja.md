```
setup_reservoir_state(model, <キーワード引数>)
# 例: 混合しない二相の場合
setup_reservoir_state(model, Pressure = 1e5, Saturations = [0.2, 0.8])
```

[`setup_reservoir_model`](@ref)を使用してセットアップされた`MultiModel`の状態を初期化する便利なコンストラクタです。[`setup_state`](@ref)に対する主な利便性は、貯留層の初期化値のみを提供する必要があることです: ウェルは接続された貯留層セルから自動的に初期化されます。

キーワード引数を渡す代わりに、`Dict{Symbol, Any}`インスタンスを第二の非キーワード引数として送信することもできます。
