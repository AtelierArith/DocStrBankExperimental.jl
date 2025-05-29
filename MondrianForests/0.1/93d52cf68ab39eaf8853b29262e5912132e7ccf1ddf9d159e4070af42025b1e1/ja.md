```
MondrianTree(d::Int, lambda::Float64)
```

次元 $d$ とパラメータ $\lambda$ を持つモンドリアンツリー $\mathcal{M}([0,1]^d, \lambda)$ をサンプリングします。

# 例

```julia
d = 2
lambda = 3.0
tree = MondrianTree(d, lambda);
```
