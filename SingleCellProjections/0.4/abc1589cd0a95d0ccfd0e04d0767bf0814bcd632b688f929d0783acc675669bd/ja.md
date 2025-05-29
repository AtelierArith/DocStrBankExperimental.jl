```
filter_obs(f, data::DataMatrix)
```

フィルターを通過した観測のみを含む新しい DataMatrix を返します。

`f` は次のいずれかです：

  * 保持するインデックスの `AbstractVector`。
  * ブール値の `AbstractVector`（保持する場合は true、破棄する場合は false）。
  * すべての観測を保持することを示す `:`。
  * `DataFrames.filter` に渡すことができる任意のもの（詳細は DataFrames のドキュメントを参照してください）。

# 例

毎回10番目の観測を保持します：

```julia
julia> filter_obs(1:10:size(data,2), data)
```

"celltype" が "other" に等しい観測を削除します：

```julia
julia> filter_obs("celltype"=>!isequal("other"), data)
```

関連情報: [`filter_matrix`](@ref), [`filter_var`](@ref), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
