```
emd(a::Union{PyObject, Array{Float64}}, b::Union{PyObject, Array{Float64}}, M::Union{PyObject, Array{Float64}};
iter::Int64 = 1000, tol::Float64 = 1e-9, returnall::Bool=false)
```

地球移動者距離を計算します。これは次のように定義されます。

$$
D(M) = \sum_{i=1}^m \sum_{j=1}^n M_{ij} d_{ij}
$$

ここで $M \in \mathbb{R}^{m\times n}$ は基準距離行列です。このアルゴリズムは次の最適化問題を解決します。

$$
\begin{aligned}\min_{M} &\ D(M)\\\text{s.t.} & \ \sum_{i=1}^m M_{ij} = b_j\\ &\ \sum_{j=1}^n M_{ij} = a_i \end{aligned}
$$

最適化問題の内部ソルバーはネットフローソルバーです。このアルゴリズムは $\sum_i a_i = \sum_j b_j = 1$ を必要とします。
