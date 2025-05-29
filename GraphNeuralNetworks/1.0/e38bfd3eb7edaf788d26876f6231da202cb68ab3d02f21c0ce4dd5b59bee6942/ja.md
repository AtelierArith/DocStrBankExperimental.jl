```
MEGNetConv(ϕe, ϕv; aggr=mean)
MEGNetConv(in => out; aggr=mean)
```

[Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals](https://arxiv.org/pdf/1812.05055.pdf) 論文からの畳み込み。フォワードパスでは、ノード特徴 `x` とエッジ特徴 `e` を入力として受け取り、次のように更新された特徴 `x'` と `e'` を返します。

$$
\begin{aligned}
\mathbf{e}_{i\to j}'  = \phi_e([\mathbf{x}_i;\,  \mathbf{x}_j;\,  \mathbf{e}_{i\to j}]),\\
\mathbf{x}_{i}'  = \phi_v([\mathbf{x}_i;\, \square_{j\in \mathcal{N}(i)}\,\mathbf{e}_{j\to i}']).
\end{aligned}
$$

`aggr` は実行される集約を定義します。

ニューラルネットワーク `ϕe` と `ϕv` が提供されていない場合、`in` と `out` 引数から代わりに多層パーセプトロンが構築され、1つの隠れ層と `relu` 活性化が使用されます。

# 例

```julia
g = rand_graph(10, 30)
x = randn(Float32, 3, 10)
e = randn(Float32, 3, 30)
m = MEGNetConv(3 => 3)
x′, e′ = m(g, x, e)
```
