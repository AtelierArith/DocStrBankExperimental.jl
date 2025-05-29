```
subnetworks(rn::ReactionSystem)
```

反応ネットワークの各連結クラスに対応するサブネットワークを見つけます。

注意:

  * `reactioncomplexes`への以前の呼び出しによって、`rn`に`incidencemat`がすでにキャッシュされている必要があります。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
complexes,incidencemat = reactioncomplexes(sir)
subnetworks(sir)
```
