```
ot_dist(x::Union{PyObject, Array{Float64}}, y::Union{PyObject, Array{Float64}}, order::Union{Int64, PyObject}=2)
```

距離関数をノルム `order` で計算します。`dist` は $n\times m$ 行列を返し、$x\in \mathbb{R}^{n\times d}$ および $y\in \mathbb{R}^{m\times d}$ であり、返される $M\in \mathbb{R}^{n\times m}$ は次のようになります。

$$
M_{ij} = ||x_i - y_j||_{o}
$$
