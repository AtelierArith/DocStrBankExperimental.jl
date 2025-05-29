```
AGNNConv(; init_beta=1.0f0, trainable=true, add_self_loops=true)
```

Attention-based Graph Neural Network layer from paper [Attention-based Graph Neural Network for Semi-Supervised Learning](https://arxiv.org/abs/1803.03735).

The forward pass is given by

$$
\mathbf{x}_i' = \sum_{j \in N(i)} \alpha_{ij} \mathbf{x}_j
$$

where the attention coefficients $\alpha_{ij}$ are given by

$$
\alpha_{ij} =\frac{e^{\beta \cos(\mathbf{x}_i, \mathbf{x}_j)}}
                  {\sum_{j'}e^{\beta \cos(\mathbf{x}_i, \mathbf{x}_{j'})}}
$$

with the cosine distance defined by

$$
\cos(\mathbf{x}_i, \mathbf{x}_j) = 
  \frac{\mathbf{x}_i \cdot \mathbf{x}_j}{\lVert\mathbf{x}_i\rVert \lVert\mathbf{x}_j\rVert}
$$

and $\beta$ a trainable parameter if `trainable=true`.

# Arguments

  * `init_beta`: The initial value of $\beta$. Default 1.0f0.
  * `trainable`: If true, $\beta$ is trainable. Default `true`.
  * `add_self_loops`: Add self loops to the graph before performing the convolution. Default `true`.

# Examples:

```julia
# create data
s = [1,1,2,3]
t = [2,3,1,1]
g = GNNGraph(s, t)

# create layer
l = AGNNConv(init_beta=2.0f0)

# forward pass
y = l(g, x)   
```
