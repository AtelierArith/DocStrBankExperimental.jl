```
Uncertainty(name::String, distribution::Distribution{Univariate, Continuous})
```

Keyword struct for defining input uncertainties.

  * The `name` argument can be any REeopt input
  * The `distribution` argument can be any of the type `Distribution{Univariate, Continuous}` from  Distributions.jl.

### Example

```@example
u1 = Uncertainty(
    name="Financial.elec_cost_escalation_pct",
    distribution=Uniform(-0.01, 0.03)    
)
```

### Distribution types

You can view all of the possible distributions with:

```@example
subtypes(Distribution{Univariate, Continuous})
```

### Custom sample sets

For the special case of `ElectricLoad.loads_kw` we allow one to provide a sample set of load profiles. The sample set is sampled uniformly. To use this capability define an `Uncertainty` as follows:

```julia
u4 = Uncertainty(
    "ElectricLoad.loads_kw",
    [
        ones(8760) .* 8.0,  # replace these vectors with your load profile samples
        ones(8760) .* 9.0,
        ones(8760) .* 10.0,
    ]
)
```
