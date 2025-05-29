```
expect(op, ados_list; take_real=true)
```

Return a list of expectation values of the operator `op` corresponds to the reduced density operators in the given `ados_list`, namely

$$
\textrm{Tr}\left[ O \rho \right],
$$

where $O$ is the operator and $\rho$ is the reduced density operator in one of the `ADOs` from `ados_list`.

# Parameters

  * `op` : the operator $O$ to take the expectation value
  * `ados_list::Vector{ADOs}` : the list of auxiliary density operators for HEOM model
  * `take_real::Bool` : whether to automatically take the real part of the trace or not. Default to `true`

# Returns

  * `exp_val` : The expectation value
