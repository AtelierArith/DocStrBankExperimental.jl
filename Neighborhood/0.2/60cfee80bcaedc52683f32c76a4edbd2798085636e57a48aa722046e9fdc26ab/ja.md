```
search(ss, query, t::SearchType [, skip]; kwargs... ) → idxs, ds
```

検索構造 `ss` に対して、指定された `query` と検索タイプ `t` で近傍検索を実行します（[`SearchType`](@ref)を参照）。近傍のインデックス（元のデータ内）とクエリからの距離を返します。利用可能な検索タイプは次のとおりです：

  * [`NeighborNumber`](@ref)
  * [`WithinRange`](@ref)

オプションの `skip` 関数は、見つかった近傍のインデックス（元のデータ内） `skip(i)` を入力として受け取り、この近傍をスキップすべき場合は `true` を返します。

パッケージ固有のキーワードが可能です。
