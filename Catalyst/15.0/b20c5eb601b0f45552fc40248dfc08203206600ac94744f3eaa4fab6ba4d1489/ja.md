```
linkagedeficiencies(network::ReactionSystem)
```

`network`内の各サブ反応ネットワークの欠陥を計算します。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
linkage_deficiencies = linkagedeficiencies(sir)
```
