```
Optimizer(method, nn_params)
```

特定の `method` と `nn_params` のために `Optimizer` のインスタンスのキャッシュを割り当てます。

内部的には [`init_optimizer_cache`](@ref) を呼び出します。

同等のコンストラクタは次のとおりです。

```julia
Optimizer(method, nn::NeuralNetwork)
```

# 引数

オプションのキーワード引数はリトラクションです。デフォルトでは [`cayley`](@ref) です。
