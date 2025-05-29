```
hasrank(gf::GeneFunction)::Bool
```

ブール関数で、次の値を返します：

  * `gf` に非欠損の `rank` フィールドを持つ [`Taxon`](@ref) がある場合は `true`、
  * `Taxon` がない場合は `false`、
  * または `Taxon` に `rank` がない場合は `false`。
