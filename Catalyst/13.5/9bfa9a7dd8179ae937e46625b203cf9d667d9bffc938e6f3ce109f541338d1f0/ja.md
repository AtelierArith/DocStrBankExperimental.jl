```
isreversible(rn::ReactionSystem)
```

与えられた反応ネットワークが可逆かどうかを返します。

ノート：

  * `reactioncomplexes`への以前の呼び出しによって、`rn`に`incidencemat`がすでにキャッシュされている必要があります。

例えば、

```julia
sir = @reaction_network SIR begin
    β, S + I --> 2I
    ν, I --> R
end
rcs,incidencemat = reactioncomplexes(sir)
isreversible(sir)
```
