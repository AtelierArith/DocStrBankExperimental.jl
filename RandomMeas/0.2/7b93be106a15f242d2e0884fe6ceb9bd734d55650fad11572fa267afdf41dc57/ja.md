```
export_measurement_data(data::MeasurementData, filepath::String)
```

測定データを `.npz` ファイルにエクスポートします。

# 引数

  * `data::MeasurementData`: 測定結果を含む測定データオブジェクトと、オプションで LocalUnitaryMeasurementSetting 設定。
  * `filepath::String`: データがエクスポートされるファイルパス。

# 詳細

  * `measurement_results` はそのままエクスポートされます。
  * `measurement_setting` が提供されている場合、関連する `local_unitaries` が抽出され、再形成され、エクスポートに含まれます。

# 注意事項

  * エクスポートされた `.npz` ファイルには以下が含まれます：

      * `"measurement_results"`: 形状 `(NM, N)` の 2D 配列で、ここで：

          * `NM`: 設定ごとの測定数。
          * `N`: キュービット/サイトの数。
      * `"local_unitaries"` (オプション): 各サイトのユニタリ変換を表す形状 `(N, 2, 2)` の 4D 配列。

# 例

```julia

# MeasurementData オブジェクトを作成
data = MeasurementData(measurement_results; measurement_setting=measurement_setting)

# ファイルにエクスポート
export_measurement_data(data, "exported_data.npz")
```
