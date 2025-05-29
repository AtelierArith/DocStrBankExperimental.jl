```
right_to_left_mask([T=Float32,] N::Integer)
```

Create a right-to-left mask for the self-attention mechanism. The mask is a matrix of size `N x N` where the diagonal and the lower triangular part are set to zero and the upper triangular part is set to infinity.
