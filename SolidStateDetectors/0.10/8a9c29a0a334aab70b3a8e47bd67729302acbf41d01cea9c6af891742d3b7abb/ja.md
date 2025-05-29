```
run_geant4_simulation(app::Geant4.G4JLApplication, number_of_events::Int; energy_threshold::Unitful.Energy)
```

指定された `Geant4.G4JLApplication` をシミュレートし、非ゼロエネルギー沈着が生成されるまで `number_of_events` イベントを生成します。

## 引数

  * `app::Geant4.G4JLApplication`: 検出器のセットアップと粒子源に関する情報を含みます。
  * `number_of_events::Int`: 検出器内で記録されるべきイベントの数。

## キーワード

  * `energy_threshold::Unitful.Energy`: 記録されるイベントの合計エネルギーに対する下限を定義します。デフォルトは `eps(Float64)*u"keV"` で、すなわち非ゼロの沈着があるすべてのイベントが記録されます。 `0u"keV"` に設定すると、すべての一次イベントが記録されます。

## 例

```julia
run_geant4_simulation(app, 1000)
# => `evtno`、`detno`、`thit`、`edep`、および `pos` フィールドを持つ `TypedTables.Table` で全イベントを返します。
```

!!! 注     関数は十分なイベントが収集されるまで実行されるため、ソースが検出器を照射しないセットアップは無限に実行されます。
