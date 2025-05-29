```
isreversible(rn::ReactionSystem)
```

Given a reaction network, returns if the network is reversible or not.

For example,

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
isreversible(sir)
```
