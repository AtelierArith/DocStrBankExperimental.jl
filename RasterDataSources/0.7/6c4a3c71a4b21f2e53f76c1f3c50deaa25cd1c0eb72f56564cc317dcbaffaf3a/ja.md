```
getraster(T::Type{CHELSA{Future{Climate}}}, [layer]; date, month) => String
```

CHELSA [`Climate`](@ref) データをダウンロードし、レイヤーを次の中から選択します: `(1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19)`。

モデルの選択については、[`Future`](@ref) のドキュメントを参照してください。

レイヤー引数を指定しない場合、すべてのレイヤーがダウンロードされ、パスの `NamedTuple` が返されます。

## キーワード

  * `date`: `Date` または `DateTime` オブジェクト、ベクター、または開始/終了日の日付のタプル。CHELSA CMIP5 には2041-2060年と2061-2080年の2つのデータセットしかありません。CMIP6 には2011-2040年、2041-2070年、2071-2100年の期間のデータセットがあります。日付はこれらの範囲内である必要があります。
  * `month`: 年の月、1から12まで、または `1:12` のような月の配列または範囲。

## 例

```
using Dates, RasterDataSources
getraster(CHELSA{Future{Climate, CMIP6, GFDLESM4, SSP370}}, :prec; date = Date(2050), month = 1)
```
