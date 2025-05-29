`OptimizationAlgorithm`は、異なるアルゴリズムをディスパッチするために使用されるデータ構造です。

次の3つの重要なメソッドを実装する必要があります。

```
initialize!(alg::OptimizationAlgorithm, ::AbstractVector)
update!(alg::OptimizationAlgorithm, ::AbstractVector)
solver_step!(::AbstractVector, alg::OptimizationAlgorithm)
```

これらは、アルゴリズムの状態を初期化および更新し、実際の最適化ステップを実行します。

さらに、次の便利なメソッドも実装する必要があります。

```
objective(alg::OptimizationAlgorithm)
gradient(alg::OptimizationAlgorithm)
hessian(alg::OptimizationAlgorithm)
linesearch(alg::OptimizationAlgorithm)
```

これらは、最適化する目的、目的の勾配、および（近似的な）ヘッセ行列、さらに最適化アルゴリズムと併用されるラインサーチアルゴリズムを返します。
