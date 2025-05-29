```
isweaklyreversible(rn::ReactionSystem, subnetworks)
```

与えられたサブネットワークを持つ反応ネットワークが弱可逆であるかどうかを判断します。

ノート：

  * `incidencemat`が以前の`reactioncomplexes`の呼び出しによって`rn`にキャッシュされている必要があります。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
subnets = subnetworks(rn)
isweaklyreversible(rn, subnets)
```
