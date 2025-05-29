```
`build_blp_model(bfp::BilevelFlowProblem, solver; comp_method)`
```

Build the JuMP model from the data of `bfp` and assign it the passed solver. Return `(m, r, y, f, λ, s)`

  * `m`: `JuMP.Model`
  * `y[i,j,k]`: binary variables indicating which option tax option is chosen by the upper-level
  * `r[i,j]`: auxiliary variable storing the revenue made on arc `[i,j]`
  * `f[i,j]`: flow variables (lower level)
  * `λ`: flattened dual vector
  * `s`: flattened slack variables for the flow problem
