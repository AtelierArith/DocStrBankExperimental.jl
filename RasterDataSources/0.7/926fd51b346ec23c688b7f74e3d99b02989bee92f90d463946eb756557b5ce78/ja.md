```
getraster(T::Type{CHELSA{Future{BioClim}}}, [layer]; date) => String
```

CHELSA [`BioClim`](@ref) データをダウンロードし、レイヤーを次から選択します: `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)`。

モデルの選択については、[`Future`](@ref) のドキュメントを参照してください。

レイヤー引数を指定しない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

## キーワード

  * `date`: `Date` または `DateTime` オブジェクト、ベクター、または開始/終了日の日付のタプル。CHELSA CMIP5 には2041-2060年および2061-2080年の2つのデータセットしかありません。CMIP6 には2011-2040年、2041-2070年、2071-2100年の期間のデータセットがあります。日付はこれらの範囲内でなければなりません。

## 例

```julia
using RasterDataSources, Dates
getraster(CHELSA{Future{BioClim, CMIP6, GFDLESM4, SSP370}}, 1, date = Date(2050))
```
