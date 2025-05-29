```
import_measurement_data(filepath::String; predefined_setting=nothing, site_indices=nothing)
```

アーカイブファイルから測定結果とオプションの測定設定をインポートします。

# 引数

  * `filepath::String`: 測定結果とオプションでローカルユニタリを含む`.npz`ファイルへのパス。このファイルには、少なくとも`measurement_results`フィールド（形状が`(NM, N)`の2Dバイナリ配列）が含まれている必要があり、オプションで`local_unitaries`フィールド（Nx2x2配列としてのローカルユニタリ）が含まれている場合があります。
  * `predefined_setting`（オプション）: 事前定義された`MeasurementSetting`オブジェクト。提供された場合、ファイルの設定の代わりに使用されます。
  * `site_indices`（オプション）: `local_unitaries`フィールドから`LocalUnitaryMeasurementSetting`を構築する際に使用されるサイトインデックスのベクトル（predefined_settingが提供されていない場合にのみ関連します）。提供されない場合、デフォルトのサイトインデックスが内部で生成されます。

# 戻り値

インポートされた結果と設定を含む`MeasurementData`オブジェクト。

# 例

```julia
# 事前定義された設定でインポート
setting = LocalUnitaryMeasurementSetting(local_unitaries; site_indices=siteinds("Qubit", 5))
data_with_setting = import_measurement_data("data.npz"; predefined_setting=setting)

# サイトインデックスを提供してインポート
data_with_indices = import_measurement_data("data.npz"; site_indices=siteinds("Qubit", 5))

# 追加のオプションなしでインポート
data = import_measurement_data("data.npz")
```
