```
MetropolisHastings{D}
```

`MetropolisHastings` has one field, `proposal`. `proposal` is a `Proposal`, `NamedTuple` of `Proposal`, or `Array{Proposal}` in the shape of your data. For example, if you wanted the sampler to return a `NamedTuple` with shape

```julia
x = (a = 1.0, b=3.8)
```

The proposal would be

```julia
proposal = (a=StaticProposal(Normal(0,1)), b=StaticProposal(Normal(0,1)))
```

Other allowed proposals are

```
p1 = StaticProposal(Normal(0,1))
p2 = StaticProposal([Normal(0,1), InverseGamma(2,3)])
p3 = StaticProposal((a=Normal(0,1), b=InverseGamma(2,3)))
p4 = StaticProposal((x=1.0) -> Normal(x, 1))
```

The sampler is constructed using

```julia
spl = MetropolisHastings(proposal)
```

When using `MetropolisHastings` with the function `sample`, the following keyword arguments are allowed:

  * `initial_params` defines the initial parameterization for your model. If

none is given, the initial parameters will be drawn from the sampler's proposals.

  * `param_names` is a vector of strings to be assigned to parameters. This is only

used if `chain_type=Chains`.

  * `chain_type` is the type of chain you would like returned to you. Supported

types are `chain_type=Chains` if `MCMCChains` is imported, or `chain_type=StructArray` if `StructArrays` is imported.
