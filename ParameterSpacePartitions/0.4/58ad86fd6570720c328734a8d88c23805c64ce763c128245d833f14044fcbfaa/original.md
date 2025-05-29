```
adapt!(
    chain, 
    options; 
    t_rate = .20, 
    kwargs...
)
```

Iteratively adapts the radius to achieve a target acceptance rate. The radius is adjusted according to the following factor `c`:

```julia
c = exp(λ * d_rate)
```

where `λ` is the adaption rate, and `d_rate` is the difference between the acceptance rate and target  acceptance rate.

# Arguments

  * `chain`: a chain for exploring the parameter space
  * `options`: a set of options for configuring the algorithm

# Keyword Arguments

  * `t_rate = .20`: target acceptance rate
  * `kwargs...`: keyword arguments that are not processed
