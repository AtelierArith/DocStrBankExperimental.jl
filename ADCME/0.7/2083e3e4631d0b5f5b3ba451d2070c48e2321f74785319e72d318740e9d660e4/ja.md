```
fcx(x::Union{Array{Float64,2},PyObject}, output_dims::Array{Int64,1}, 
θ::Union{Array{Float64,1}, PyObject};
activation::String = "tanh")
```

出力次元 `o` を持つ完全連結ニューラルネットワークを作成し、入力は $x\in \mathbb{R}^{m\times n}$ です。

$$
x \rightarrow o_1 \rightarrow o_2 \rightarrow \ldots \rightarrow o_k
$$

`θ` はニューラルネットワークの重みとバイアスであり、例えば `θ = ae_init(output_dims)` のようになります。

`fcx` は二つのテンソルを出力します：

  * ニューラルネットワークの出力： $u\in \mathbb{R}^{m\times o_k}$。
  * サンプルごとのニューラルネットワークの感度： $\frac{\partial u}{\partial x}\in \mathbb{R}^{m \times o_k \times n}$
