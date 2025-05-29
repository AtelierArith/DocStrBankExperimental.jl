```
X = get_subgradient(M::AbstractManifold, sgo::AbstractManifoldGradientObjective, p)
get_subgradient!(M::AbstractManifold, X, sgo::AbstractManifoldGradientObjective, p)
```

サブグラディエントを評価します。これは、勾配を持つ目的の場合、勾配自体を評価することを意味します。

一般的には、結果が決定論的でない場合もありますが、この場合はそうではありません。
