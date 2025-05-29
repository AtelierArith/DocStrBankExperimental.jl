```
decode(gc::Geocoder, points) => Array{NamedTuple{(:country, :country_code, :city), Tuple{String, String, String}}}
```

ポイントのコレクションに対して国名と都市を返します。ポイントは、静的サイズの配列の配列（例：StaticArrays）または行列である必要があります（詳細はNearestNeighbors.jlのドキュメントを参照してください）。

国と都市は、geonames.orgからの都市位置のラベル付きリストに対する最近傍探索によって決定されます。そのため、結果は正確でない場合があります（例：国境近くや人里離れた場所のポイントの検索）。

最近傍探索は、緯度/経度座標の空間におけるユークリッド距離を使用します。

```
# 例
julia> gc = Geocoder();
julia> ReverseGeocode.decode(gc, [SA[49.5863897, 17.2627342], SA[63.3342550, 12.0280064]])
2-element Array{Tuple{String,String},1}:
 (country="Czechia", country_code="CZ", city="Olomouc")
 (country="Norway", country_code="NO", city="Meråker")
```
