```
droplevels!(A::CategoricalArray)
```

カテゴリカル配列 `A` に現れないレベルを削除します（そのため、[`levels`](@ref DataAPI.levels) によって返されることはなくなります）。
