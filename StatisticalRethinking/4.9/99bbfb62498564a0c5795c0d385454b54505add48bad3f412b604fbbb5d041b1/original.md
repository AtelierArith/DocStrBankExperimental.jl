# simulate

Used for counterfactual simulations.

```julia
simulate(df, coefs, var_seq)

```

### Required arguments

```julia
* `df`                                 : DataFrame with coefficient samples
* `coefs`                              : Vector of coefficients
* `var_seq`                            : Input values for simulated effect
```

### Return values

```julia
* `m_sim::NamedTuple`                  : Array with predictions
```
