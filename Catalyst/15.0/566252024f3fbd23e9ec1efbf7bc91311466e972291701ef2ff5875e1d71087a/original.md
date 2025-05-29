```
isweaklyreversible(rn::ReactionSystem, subnetworks)
```

Determine if the reaction network with the given subnetworks is weakly reversible or not.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
subnets = subnetworks(rn)
isweaklyreversible(rn, subnets)
```
