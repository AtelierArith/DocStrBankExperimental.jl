```
get_year_idxs(data, year_idxs) -> idxs
```

`year_idxs`を`get_years(data)`にインデックスを付けるために使用できるインデックスのセットに変換します。`year_idxs`は以下のいずれかのタイプであることができます：

  * `Colon`
  * `Int64`
  * `AbstractVector{Int64}`
  * `AbstractString` - 年を表す、例："y2020"
  * `AbstractVector{<:AbstractString}` - 年を表す文字列のベクター、例："y2020"
  * `Tuple{<:AbstractString, <:AbstractString}`
  * `Function` - 年の文字列に対して真偽値を返す関数。例：<=("y2030")
