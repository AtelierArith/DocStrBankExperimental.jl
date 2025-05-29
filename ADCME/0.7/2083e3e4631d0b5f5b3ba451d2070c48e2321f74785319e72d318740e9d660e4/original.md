```
fcx(x::Union{Array{Float64,2},PyObject}, output_dims::Array{Int64,1}, 
θ::Union{Array{Float64,1}, PyObject};
activation::String = "tanh")
```

Creates a fully connected neural network with output dimension `o` and inputs $x\in \mathbb{R}^{m\times n}$. 

$$
x \rightarrow o_1 \rightarrow o_2 \rightarrow \ldots \rightarrow o_k
$$

`θ` is the weights and biases of the neural network, e.g., `θ = ae_init(output_dims)`.

`fcx` outputs two tensors:

  * the output of the neural network: $u\in \mathbb{R}^{m\times o_k}$.
  * the sensitivity of the neural network per sample: $\frac{\partial u}{\partial x}\in \mathbb{R}^{m \times o_k \times n}$
