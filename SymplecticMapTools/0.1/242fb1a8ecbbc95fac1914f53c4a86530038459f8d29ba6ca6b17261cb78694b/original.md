```
kernel_sample_F(F::Function, N::Integer, xb::AbstractVector,
                yb::AbstractVector)
```

Sobol sample `N` points in the rectangle `xb` × `yb`. Then, evaluate `F` at each point. Input can be used for `kernel_eigs` and `kernel_bvp`

Arguments:

  * `F`: The symplectic map from the state space to itself
  * `N`: The number of points to be sampled
  * `xb` × `yb`: The 2-vector bounds of the rectangle to be sampled

Output:

  * `xs`: A `2` × `2N` array of samples compatable with `kernel_eigs` and `kernel_bvp`, of the form `[x_1, F(x_1), x_2, F(x_2), ...]`
