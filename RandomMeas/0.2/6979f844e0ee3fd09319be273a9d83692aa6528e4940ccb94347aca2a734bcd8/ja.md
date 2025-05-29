```
import_MeasurementGroup(filepath::String; predefined_settings=nothing, site_indices=nothing) -> MeasurementGroup
```

NPZファイルからMeasurementGroupオブジェクトをインポートします。

# 引数

  * `filepath::String`: エクスポートされたMeasurementGroupデータを含むNPZファイルへのパス。
  * `predefined_settings`（オプション）: 事前定義された測定設定のベクター（MeasurementDataオブジェクトごとに1つ）。提供された場合、その長さはエクスポートされたNUと等しくなければなりません。
  * `site_indices`（オプション）: 測定設定を再構築する際に使用するN個のサイトインデックスのベクター。提供されない場合、デフォルトのサイトインデックスは`siteinds("Qubit", N)`を使用して生成されます。

# 戻り値

次の内容を持つMeasurementGroupオブジェクト:

  * 形状(NU, NM, N)の3D配列から再構築された測定結果。
  * 存在する場合、形状(NU, N, 2, 2)の4D配列から再構築された各MeasurementDataオブジェクトの測定設定、または提供された場合は`predefined_settings`から取得されます。
