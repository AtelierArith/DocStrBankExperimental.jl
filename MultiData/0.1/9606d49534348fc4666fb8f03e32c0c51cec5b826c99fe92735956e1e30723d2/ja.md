```
ninstances(md)
```

マルチモーダルデータセット内のインスタンスの数を返します。

# 例

```julia-repl
julia> md = MultiDataset([[1],[2]],DataFrame(:age => [25, 26], :sex => ['M', 'F']))
● MultiDataset
   └─ 次元数: (0, 0)
- モダリティ 1 / 2
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ age
     │ Int64
─────┼───────
   1 │    25
   2 │    26
- モダリティ 2 / 2
   └─ 次元数: 0
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> mod2 = modality(md, 2)
2×1 SubDataFrame
 Row │ sex
     │ Char
─────┼──────
   1 │ M
   2 │ F

julia> ninstances(md) == ninstances(mod2) == 2
true
```
