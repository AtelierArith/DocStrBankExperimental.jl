植生期間の開始日と終了日を、日平均気温と年の日数（DOY）に基づいて計算します。植生期間内の日度の合計を便利のために含めることができます。

植生期間の開始と終了を決定するための一般的な方法が提供されており、詳細は各メソッドのドキュメントを参照してください。ドイツの森林樹木に関する人気の選択肢は `Menzel` と `vonWilpert` です。NW-FVAでの気候変動影響研究は、しばしば `Menzel` を「Picea abies (frueh)」で、すべての樹種に対して `NuskeAlbert` を使用して実施されており、樹種の特性はその後の統計モデルで考慮されています。

利用可能なメソッドは `subtypes(VegetationStartMethod)` と `subtypes(VegetationEndMethod)` で照会できます。

引数:

  * `dates` はカレンダー日付のベクター（`Date` クラスのオブジェクト）です。`est_prev > 0` の場合は完全な年を含む必要があります。それ以外の場合、最初の年は11月と12月のみを含むことができます。
  * `Tavg` は摂氏の1日あたりの平均気温のベクターです。`dates` と同じ長さです。
  * `start_method` は VegetationStartMethod です。
  * `end_method` は VegetationEndMethod です。
  * `Tsum_out` はブール値です。植生期間内の `Tsum_crit` を超える日平均気温の合計を返します。これは成長日度とも呼ばれます。
  * `Tsum_crit` は日度の合計の閾値です。`Tsum_crit` を超える日平均気温のみが集計されます。デフォルトの `0` は、負の気温が合計を減少させるのを防ぎます。気候変動研究では、しばしば `5` の閾値が使用されます。
  * `check_data` はブール値です。温度データの妥当性チェックを実施します。妥当な範囲は -35 から +40°C です。

戻り値: 入力データの（各）年の植生期間の開始日と終了日の年、日付、DOYを含む `DataFrame`。

例:

```
dates   = Date("2018-01-01"):Day(1):Date("2022-12-31")
Tavg    = 
    30 * (0.3 .+ 1/2*cos.(dayofyear.(dates)/365 * 2π .- π)) .+ 
    rand([-34.9 : 0.1 : 39.9;]/10, length(dates))

vegperiod(
    dates, 
    Tavg, 
    Menzel("Picea abies (frueh)", est_prev = 2), 
    VonWilpert())
```
