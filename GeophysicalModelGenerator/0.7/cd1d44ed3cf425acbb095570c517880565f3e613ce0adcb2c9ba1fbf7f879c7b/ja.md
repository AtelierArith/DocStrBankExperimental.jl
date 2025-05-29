```
Phase = compute_phase(Phase, Temp, X, Y, Z, s::LithosphericPhases, Ztop)
```

または

```
Phase = compute_phase(Phase, Temp, Grid::AbstractGeneralGrid, s::LithosphericPhases)
```

これは層状リソスフェアをPhase行列にコピーします。

# パラメータ

  * Phase - フェーズ配列
  * Temp  - 温度配列
  * X     - x座標配列（PhaseおよびTempと一致）
  * Y     - y座標配列（PhaseおよびTempと一致）
  * Z     - 垂直座標配列（PhaseおよびTempと一致）
  * s     - リソスフェアフェーズ
  * Ztop  - モデルボックスの上部の垂直座標
  * Grid  - グリッド構造（通常はread*LaMEM*inputfileで取得）
