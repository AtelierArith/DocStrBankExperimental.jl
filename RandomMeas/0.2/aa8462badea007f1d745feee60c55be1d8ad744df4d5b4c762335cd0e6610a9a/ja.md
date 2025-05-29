```
MeasurementGroup{T}
```

実際のまたはシミュレーションされた量子実験で使用される測定データオブジェクトのグループのコンテナ。

# フィールド

  * `N::Int`: サイト数（キュービット）。
  * `NU::Int`: 測定データオブジェクトの数。
  * `NM::Int`: 設定ごとの測定数。
  * `measurements::Vector{MeasurementData{T}}`: 測定データオブジェクトのベクター。

# 型パラメータ

  * `T`: 各測定データオブジェクトの測定設定の型で、`Union{Nothing, AbstractMeasurementSetting}`に制約される。

# 使用法

通常、提供されたコンストラクタのいずれかを介して構築される。

# 例

```julia
# setting1とsetting2が有効な測定設定であると仮定する
data1 = MeasurementData(results1; measurement_setting=setting1)
data2 = MeasurementData(results2; measurement_setting=setting2)
group = MeasurementGroup([data1, data2])
```
