```
eval_gsa(m::Chain, x, n::Int = min(10000,size(x,1)))
```

Global sensitivity analysis (GSA) with the Morris Method.

Reference: https://book.sciml.ai/notes/17-Global*Sensitivity*Analysis/

Reference: https://docs.sciml.ai/GlobalSensitivity/stable/methods/morris/

**Arguments:**

  * `m`: neural network model
  * `x`: `N` x `Nf` data matrix (`Nf` is number of features)
  * `n`: (optional) number of samples (instances) to use for explanation

**Returns:**

  * `means`: means of elementary effects
