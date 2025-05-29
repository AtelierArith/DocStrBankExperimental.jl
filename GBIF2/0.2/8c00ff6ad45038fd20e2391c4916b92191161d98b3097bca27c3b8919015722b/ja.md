```
occurrence_inventory(type::Symbol; kw...)
```

特定の基準に基づいて分類群の出現回数を返します。返り値はJSON3.jlオブジェクトです。

# 例

```
julia> country_counts = occurrence_inventory(:countries)
JSON3.Object{Vector{UInt8}, Vector{UInt64}} with 252 entries:
  :UNITED_STATES  => 816855696
  :CANADA         => 133550183
  :FRANCE         => 119683053
  :SWEDEN         => 116451484
  :AUSTRALIA      => 115239040
  :UNITED_KINGDOM => 108417142
  :NETHERLANDS    => 85750415
  :SPAIN          => 54804973
  :DENMARK        => 49334935
  :GERMANY        => 49290658
  :NORWAY         => 48337823
  :FINLAND        => 36970838
  :BELGIUM        => 35064346
  :SOUTH_AFRICA   => 33185318
  :INDIA          => 32071907
  :MEXICO         => 26295593
  :BRAZIL         => 24558941
  :COSTA_RICA     => 21103286
  :COLOMBIA       => 20143253
  :SWITZERLAND    => 17727317
  :PORTUGAL       => 17688228
  ⋮               => ⋮

julia> country_counts.INDIA
32071907
```

# キーワード

  * `type`: カテゴリ間のインベントリで、追加のキーワードは次の通りです：

`(basisOfRecord = (), countries = :publishingCountry, datasets = (:country, :taxonKey), publishingCountry = (:publishingCountry,), year = (:year,))`

出現回数のカウントには許可されたキーワードの組み合わせの複雑なスキーマがあります。これらは`occurrence_count_schema()`を使用してGBIF APIからアクセスできます。
