```
TwoBinaryTraitSubstitutionModel(rate [, label])
```

[`TraitSubstitutionModel`](@ref) for two binary traits, possibly correlated. Default labels are "x0", "x1" for trait 1, and "y0", "y1" for trait 2. If provided, `label` should be a vector of size 4, listing labels for trait 1 first then labels for trait 2. `rate` should be a vector of substitution rates of size 8. rate[1],...,rate[4] describe rates of changes in trait 1. rate[5],...,rate[8] describe rates of changes in trait 2. In the transition matrix, trait combinations are listed in the following order: x0-y0, x0-y1, x1-y0, x1-y1.

# example

```julia
model = TwoBinaryTraitSubstitutionModel([2.0,1.2,1.1,2.2,1.0,3.1,2.0,1.1],
        ["carnivory", "noncarnivory", "wet", "dry"]);
model
using PhyloPlots
plot(model) # to visualize states and rates. not supported with PhyloPlots v2.0.0. requires PhyloPlots v1.0.0
```
