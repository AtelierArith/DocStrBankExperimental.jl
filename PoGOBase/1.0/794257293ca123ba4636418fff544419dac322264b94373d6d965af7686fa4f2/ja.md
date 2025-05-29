```
Pokemon(id, level, ivs; name=display_name(id), islucky=false, mutation='N', isshiny=false, mega=false, max='N', maxlevel=nothing, raid_tier=nothing, max_tier=nothing)
Pokemon(id, ivs; cp, kwargs...)
```

ポケモンを構築します。`id` は `Species` か、`only_pokemon(id; exact=true)` の有効な引数です。`level` が指定されていない場合、`cp` は必須のキーワード引数です。`mega` は通常 `true` または `false` ですが、メガ進化を明確にするために `Char` を指定する必要がある場合（例えば、リザードンの場合）もあります（例：`'X'` または `'Y'`）。

# 例

```julia
julia> Pokemon("Ralts", (8, 12, 10); cp=204)
Ralts; CP: 204; level: 15.0; IVs: (8, 12, 10)

julia> Pokemon("LUCARIO", 20.0, (15, 12, 13); name="Wiley")
Wiley (Lucario); CP: 1521; level: 20.0; IVs: (15, 12, 13)
```
