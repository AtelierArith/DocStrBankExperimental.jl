```
merge_var(fs; vars=nothing, var=nothing,
    progress=true, box::Union{bbox,Nothing}=nothing)
```

# 引数

  * `fs`: tiffファイルのパス
  * `vars`: tiff内の変数
  * `var`: マージする変数

# 例

```julia
box = bbox(-180, -60, 180, 90)
```
