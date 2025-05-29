```
filter_matrix(fvar, fobs, data::DataMatrix)
```

フィルターを通過する変数と観測値のみを含む新しい DataMatrix を返します。

`fvar`/`fobs` は次のいずれかです：

  * 保持するインデックスの `AbstractVector`。
  * ブール値の `AbstractVector`（保持する場合は true、破棄する場合は false）。
  * すべての変数/観測値を保持することを示す `:`。
  * `DataFrames.filter` に渡すことができる任意のもの（詳細については [DataFrames ドキュメント](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter) を参照）。

また、DataMatrix のインデックス付けはインデックス/ブール値の `AbstractVector` と `:` をサポートし、それ以外は `filter_matrix` と同じです。

# 例

毎回10番目の変数と3番目の観測値を保持します：

```julia
julia> filter_matrix(1:10:size(data,1), 1:3:size(data,2), data)
```

または、インデックス構文を使用して：

```julia
julia> data[1:10:end, 1:3:end]
```

さらに例については、`filter_var` と `filter_obs` を参照してください。

参照： [`filter_var`](@ref)、[`filter_obs`](@ref)、[`DataFrames.filter`](https://dataframes.juliadata.org/stable/lib/functions/#Base.filter)
