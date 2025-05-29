```
incidencematgraph(rn::ReactionSystem)
```

反応複合体に対応するノードと、2つの複合体間を変換する反応に対応する有向エッジを持つ有向単純グラフを構築します。

注意:

  * `reactioncomplexes`への以前の呼び出しによって、`rn`に`incidencemat`がすでにキャッシュされている必要があります。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
complexes,incidencemat = reactioncomplexes(sir)
incidencematgraph(sir)
```
