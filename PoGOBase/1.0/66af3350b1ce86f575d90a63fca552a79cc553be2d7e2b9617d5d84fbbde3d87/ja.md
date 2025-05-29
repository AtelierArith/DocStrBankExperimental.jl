```
league_max_level(poke::Pokemon, league_cp::Int; level_limit=50.0) → level, cp
league_max_level(poke::Pokemon, level::Real, league_cp::Int; level_limit=50.0) → level, cp
league_max_level(name::AbstractString, ivs, level, league_cp::Int; level_limit=50.0) → level, cp
```

`league_cp`以下に保つための最大の`level`と対応する`cp`を返します。`poke.level`がすでに高すぎる場合はエラーになりますが、希望する場合は手動で代替の`level`を指定することができます（1.0は最も多くの機会を提供するため良い選択です）。
