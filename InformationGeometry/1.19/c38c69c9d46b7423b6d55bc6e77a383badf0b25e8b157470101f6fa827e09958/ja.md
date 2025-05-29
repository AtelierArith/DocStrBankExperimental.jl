```
KullbackLeibler(p::Function,q::Function,Domain::HyperCube=HyperCube([-15,15]); tol=2e-15, N::Int=Int(3e7), Carlo::Bool=(length(Domain)!=1))
```

確率分布 `p` と `q` の間のクルバック・ライブラー発散を `Domain` 上で計算します。`Carlo=true` の場合、これは `N` サンプルを用いたモンテカルロシミュレーションを使用して行われます。`Domain` が一次元の場合、計算はモンテカルロなしでおおよそ `tol` の許容誤差で行われます。

$$
D_{\text{KL}}[p,q] \coloneqq \int \mathrm{d}^m y \, p(y) \, \mathrm{ln} \bigg( \frac{p(y)}{q(y)} \bigg)
$$
