```
group_block_objective(Σ, S, groups, m, method)
```

Evaluate the objective for SDP/MVR/ME. This is not an efficient function, so it should only be called at the start of each algorithm. 

# Inputs

  * `Σ`: Covariance or correlation matrix for original data
  * `S`: Optimization variable (group-block-diagonal)
  * `groups`: Vector of group membership. Variable `i` belongs to group `groups[i]`
  * `m`: Number of knockoffs to generate for each variable
  * `method`: The optimization method for group knockoffs
