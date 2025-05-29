```
MAPGPOptimizer(; every = 10, kwargs...)
```

GPのハイパーパラメータを最大事後確率（MAP）推定値に`every`ステップごとに設定します。デフォルトのオプションを確認するには、`BayesianOptimization.defaultoptions(MAPGPOptimizer)`を実行してください。デフォルトでは、すべての事前分布はフラットです。区間内の一様事前分布は、`[lowerbound, upperbound]`の形式で境界を設定することで指定できます。たとえば、3つのパラメータを持つカーネルの場合、`kernbounds = [[-3, -3, -4], [2, 3, 1]]`のように設定します。非フラットな事前分布は、GPパラメータに直接指定できます。たとえば、`using Distributions; set_priors!(mean, [Normal(0., 1.)])`のようにします。
