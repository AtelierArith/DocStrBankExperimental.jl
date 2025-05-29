```
pseudobulk(data::DataMatrix, obs_col, [additional_columns...]; var=:copy)
```

グループに対して平均を取ることによって新しい `DataMatrix` を作成します。グループはカテゴリカルアノテーション `obs_col`（およびオプションで追加の列）によって指定されます。

  * `var` - `:copy`（ソース `var` のコピーを作成）または `:keep`（ソース `var` オブジェクトを共有）にできます。

# 例

各サンプルの擬似バルク表現を作成します：

```julia
julia> pseudobulk(transformed, "sampleName")
```

各サンプルの各細胞型の擬似バルク表現を作成します：

```julia
julia> pseudobulk(transformed, "sampleName", "celltype")
```
