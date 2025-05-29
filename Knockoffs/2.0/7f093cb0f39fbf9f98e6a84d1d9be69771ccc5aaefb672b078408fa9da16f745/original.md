```
solve_sdp_ccd(Σ::AbstractMatrix)
```

Solves the SDP problem for fixed-X and model-X knockoffs using coordinate descent,  given correlation matrix Σ. Users should call `solve_s` instead of this function. 

# Reference

Algorithm 2.2 from "FANOK: Knockoffs in Linear Time" by Askari et al. (2020).
