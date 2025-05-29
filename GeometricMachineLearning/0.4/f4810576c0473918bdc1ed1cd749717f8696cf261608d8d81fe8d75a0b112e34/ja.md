```
GradientOptimizer(η)
```

勾配最適化器のインスタンスを作成します。

これは最も単純なニューラルネットワークの最適化器です。キャッシュはなく、最終的な速度は次のように計算されます：

$$
    \mathrm{velocity} \gets - \eta\nabla_\mathrm{weight}L.
$$

# 実装

操作は可能な限りメモリ効率よく行われます。これは、提供された $\nabla_WL$ が次のように変異されることを意味します：

```julia
rmul!(∇L, -method.η)
```
