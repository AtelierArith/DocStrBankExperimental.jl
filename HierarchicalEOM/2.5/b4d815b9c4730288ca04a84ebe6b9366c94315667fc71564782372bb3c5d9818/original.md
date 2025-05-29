```
expect(op, ados; take_real=true)
```

Return the expectation value of the operator `op` for the reduced density operator in the given `ados`, namely

$$
\textrm{Tr}\left[ O \rho \right],
$$

where $O$ is the operator and $\rho$ is the reduced density operator in the given ADOs.

# Parameters

  * `op` : the operator $O$ to take the expectation value
  * `ados::ADOs` : the auxiliary density operators for HEOM model
  * `take_real::Bool` : whether to automatically take the real part of the trace or not. Default to `true`

# Returns

  * `exp_val` : The expectation value
