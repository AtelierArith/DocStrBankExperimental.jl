```
@rotate_orbs(orb1, orb2, angle, kwargs...)
```

軌道 `orb1` と `orb2` を [`WfOptions.orb`](@ref ECInfos.WfOptions) から `angle`（度単位）だけ回転させます。UHFの場合、`spin` は `:α` または `:β`（キーワード引数）にできます。

軌道は [`WfOptions.orb`](@ref ECInfos.WfOptions) に保存されます。

# キーワード引数

  * `spin::Symbol`: 軌道のスピン（デフォルト: `:α`）。

# 例

```julia
@dfhf
# 軌道 1 と 2 を入れ替える
@rotate_orbs 1, 2, 90
```
