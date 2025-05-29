```
modelpredict(data::RheoTimeData, model::RheoModel; diff_method="BD")
```

不完全なデータセット（応力またはひずみのいずれかが欠けている）とパラメータに値が代入されたモデル（`RheoModel`）を考慮して、モデルに基づいて新しいデータセットを返します。データが`stress_only`タイプの場合、クリープ弾性率が使用されます。データが`strain_only`タイプの場合、緩和弾性率が使用されます。完全な`RheoTimeData`の`strain_and_stress`タイプが返されます。`diff_method`は、遺伝的積分で使用される導関数を計算するための有限差分を設定し、後方差分（`"BD"`）または中央差分（`"CD"`）のいずれかを指定できます。
