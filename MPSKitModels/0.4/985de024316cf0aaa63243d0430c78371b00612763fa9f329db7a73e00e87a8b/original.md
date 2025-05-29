```
@mpoham(block)
```

Specify a Matrix Product Operator that is represented by a sum of local operators.

This macro converts expressions of the form `O{i...}` to an operator acting on sites `i...` where `O` is an operator, and `i` can be an integer or a lattice point. The macro recognizes expressions of the following forms:

  * `O{i...}` to indicate local operators `O` acting on sites `i...`
  * `-Inf:Inf`, `-∞:∞`, `-Inf:step:Inf`, `-∞:step:∞` to indicate infinite chains.
  * `1:L` to indicate finite chains.
  * `∑` to represent sums.

# Examples

```julia
H_ising = @mpoham sum(σᶻᶻ{i, i+1} + h * σˣ{i} for i in -Inf:Inf)
H_heisenberg = @mpoham ∑(sigma_exchange(){i,j} for (i,j) in nearest_neighbours(-∞:∞))
```
