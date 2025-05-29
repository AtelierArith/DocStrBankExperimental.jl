```
linkagedeficiencies(network::ReactionSystem)
```

Calculates the deficiency of each sub-reaction network within `network`.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
linkage_deficiencies = linkagedeficiencies(sir)
```
