```
isweaklyreversible(rn::ReactionSystem, subnetworks)
```

与えられたサブネットワークを持つ反応ネットワークが弱可逆であるかどうかを判断します。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
subnets = subnetworks(rn)
isweaklyreversible(rn, subnets)
```
