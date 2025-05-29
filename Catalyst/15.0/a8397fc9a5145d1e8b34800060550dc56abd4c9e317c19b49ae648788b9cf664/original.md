```
subnetworks(rn::ReactionSystem)
```

Find subnetworks corresponding to each linkage class of the reaction network.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
subnetworks(sir)
```
