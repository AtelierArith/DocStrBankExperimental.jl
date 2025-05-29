```
linkagedeficiencies(network::ReactionSystem)
```

`network`内の各サブ反応ネットワークの欠陥を計算します。

注意:

  * `reactioncomplexes`への以前の呼び出しによって、`rn`に`incidencemat`がすでにキャッシュされている必要があります。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
linkage_deficiencies = linkagedeficiencies(sir)
```
