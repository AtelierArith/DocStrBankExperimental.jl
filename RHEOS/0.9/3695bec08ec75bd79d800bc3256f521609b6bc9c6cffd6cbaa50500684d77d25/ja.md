```
modelsteppredict(data::RheoTimeData, model::RheoModel; step_on::Real = 0.0)
```

`modelpredict`と同様ですが、`step_on`で指定された値またはその指定された値に最も近い実際の値でステップが始まるステップ荷重を仮定します。荷重データが変動する場合、配列の中央の大きさが使用されます。
