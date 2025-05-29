```
Lineage{T<:AbstractTaxon} <: AbstractVector{T}
```

`Vector`のような形式で系統情報を格納する型です。`T`は要素の型、`Taxon`または`UnclassifiedTaxon`を表します。

  * `getindex`は`Taxon`値を取得するためにオーバーロードされています。`CanonicalRanks`内の`:superkingdom`、`:family`、`:genus`、`:species`のような`Symbol`を使用できます。また、より複雑なランク選択シナリオでは、`Between`、`From`、`Until`、`Cols`、および`All`セレクタを使用できます。
  * 一度再フォーマットされると、再フォーマットすることはできません。ステータスは`isreformatted(lineage)`を使用して確認できます。
