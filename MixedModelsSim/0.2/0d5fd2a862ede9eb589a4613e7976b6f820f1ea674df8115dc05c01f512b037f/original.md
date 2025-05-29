```
createθ(m::MixedModel; named_re)
create_theta(m::MixedModel; named_re)
```

Create the parameter vector θ corresponding to the random effects.

The `named_re` can be created using [`create_re`](@ref). The `named_re` are specified by the name of the blocking variable, e.g. `subj=create_re(...)`.

The model must be specified because the parameters are sorted internally for computational efficiency.
