```
readnl(xlims = X(Rasters.Between(65.39, 99.94)), ylims = Y(Rasters.Between(5.34, 39.27)), start_date = Date(2012, 04), end_date = Date(2023, 01))
```

特定のディレクトリから夜間光データを読み込み、放射とカバレッジを表す2つのラスタシリーズを返します。

# 引数

  * `xlims`: X座標の制限を定義する `X(Rasters.Between(min, max))` のインスタンス。デフォルトは `X(Rasters.Between(65.39, 99.94))` です。
  * `ylims`: Y座標の制限を定義する `Y(Rasters.Between(min, max))` のインスタンス。デフォルトは `Y(Rasters.Between(5.34, 39.27))` です。
  * `start_date`: データを読み込む期間の開始日（含む）。`Date` のインスタンスである必要があります。デフォルトは `Date(2012, 04)` です。
  * `end_date`: データを読み込む期間の終了日（含む）。`Date` のインスタンスである必要があります。デフォルトは `Date(2023, 01)` です。

# 戻り値

2つのデータキューブ。最初のキューブには放射データが含まれ、2番目のキューブにはカバレッジデータが含まれます。各データキューブには、start*date から end*date までのデータが含まれ、昇順にソートされています。

# 例

```julia
using Rasters
xlims = X(Rasters.Between(65.39, 75.39))
ylims = Y(Rasters.Between(5.34, 15.34))
start*date = Date(2015, 01)
end*date = Date(2020, 12)
rad*dc, cf*dc = readnl(xlims, ylims, start*date, end*date)
```
