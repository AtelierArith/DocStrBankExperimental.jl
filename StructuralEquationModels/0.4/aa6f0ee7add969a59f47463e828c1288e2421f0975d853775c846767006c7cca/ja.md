`ProximalAlgorithms.jl`に接続し、最適化バックエンドとして使用されます。正則化されたSEMに使用でき、チュートリアルについては[Regularization](@ref)のオンラインドキュメントを参照してください。

# コンストラクタ

```
SemOptimizerProximal(;
    algorithm = ProximalAlgorithms.PANOC(),
    operator_g,
    operator_h = nothing,
    kwargs...,
```

# 引数

  * `algorithm`: 最適化アルゴリズム。
  * `operator_g`: プロキシマルオペレーター（例：正則化ペナルティ）
  * `operator_h`: オプションの第二プロキシマルオペレーター

# 使用法

`ProximalAlgorithms.jl`のすべてのアルゴリズムとオペレーターが利用可能で、詳細については[Regularization](@ref)のオンラインドキュメントおよび`ProximalAlgorithms.jl` / `ProximalOperators.jl`のドキュメントを参照してください。
