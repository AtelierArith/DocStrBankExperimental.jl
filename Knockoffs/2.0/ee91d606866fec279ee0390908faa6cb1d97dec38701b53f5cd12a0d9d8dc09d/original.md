```
simulate_block_covariance(groups, ρ, γ, num_v, w)
```

Simulates a block covariance matrix similar to the one in `Dai & Barber 2016,  The knockoff filter for FDR control in group-sparse and multitask regression`.  That is, all diagonal elements will be 1, correlation within groups will be `ρ`, and correlation between groups will be `ρ*γ`. 

# Inputs

  * `groups`: Vector of group membership
  * `ρ`: within group correlation
  * `γ`: between group correlation

# Optional arguments

  * `num_v`: Number of added rank 1 update `Σ + v1*v1' + ... + vn*vn'` where `v`    is iid `N(0, w)` (default 0)
  * `w`: variance of the rank 1 update used in `num_v` (default 1)
