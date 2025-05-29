```
FilteringProblem(state_model, obs_model)
```

隠れ状態モデル `state_model` と観測モデル `obs_model` のフィルタリング問題を指定します。

制約: `state_model` と `obs_model` は次のように選択する必要があります。

  * `state_model` は型 `HiddenStateModel{S1, T1}` であること、
  * `obs_model` は型 `ObservationModel{S1, S2, T2}` であること、

ここで、`T1<:TimeType`、`T2 <:TimeType`、および `S1`、`S2` は任意です。これにより、フィルタリング問題が評価可能であることが保証されます。すなわち、隠れ状態は観測を生成するのに適切な型である必要があります。
