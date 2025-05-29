```
filter_var(f, data::DataMatrix; kwargs...)
```

フィルターを通過する変数のみを含む新しい DataMatrix を返します。

`f` は次のいずれかです：

  * 保持するインデックスの `AbstractVector`。
  * ブール値の `AbstractVector`（保持する場合は true、破棄する場合は false）。
  * すべての変数を保持することを示す `:`。
  * `DataFrames.filter` に渡すことができる任意のもの（詳細については [DataFrames ドキュメント](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) を参照してください）。

# 例

毎回10番目の変数を保持します：

```julia
julia> filter_var(1:10:size(data,1), data)
```

タイプ "Gene Expression" の変数のみを保持します：

```julia
julia> filter_var("feature_type"=>isequal("Gene Expression"), data)
```

関連情報: [`filter_matrix`](@ref), [`filter_obs`](@ref), [`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
