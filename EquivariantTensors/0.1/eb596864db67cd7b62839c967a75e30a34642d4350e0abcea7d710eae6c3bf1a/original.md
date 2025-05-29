`struct PooledSparseProduct` :  This implements a fused (tensor) product and pooling operation. Suppose  we are given $N$ embeddings $\phi^{(i)}_{k_i}$ then the pooled sparse product  generates feature vectors of the form 

$$
A_{k_1, \dots, k_N} = \sum_{j} \prod_{t = 1}^N \phi^{(t)}_{k_t}(x_j)
$$

where $x_j$ are an list of inputs (multi-set). 

The canonical example is 

$$
A_{nlm} = \sum_{j} R_{nl}(r_j, \mu_j) Y_l^m( \hat{\bm r}_j ),
$$

where $R_{nl}$ is a radial embedding, possibly depending on a categorical  variable $\mu_j$ and $Y_l^m$ are spherical harmonics. 

### Constructor

```julia
PooledSparseProduct(spec)
```

where `spec` is a list of $(k_1, \dots, k_N)$ tuples or vectors, or  `AbstractMatrix` where each column specifies such a tuple. 
