# simulate

Counterfactual predictions after manipulating a variable.

```julia
simulate(df, coefs, var_seq, coefs_ext)

```

### Required arguments

```julia
* `df`                                 : DataFrame with coefficient samples
* `coefs`                              : Vector of coefficients
* `var_seq`                            : Input values for simulated effect
* `ext_coefs`                          : Vector of simulated variable coefficients
```

### Return values

```julia
* `(m_sim, d_sim)`                     : Arrays with predictions
```
