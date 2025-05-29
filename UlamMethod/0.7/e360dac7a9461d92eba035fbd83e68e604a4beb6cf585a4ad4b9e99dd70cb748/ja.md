```
struct StationaryReinjection
```

定常分布 `P_open` によって重み付けされたデータを再注入します。

### フィールド

  * `fallback`: 定常分布を計算できない場合に適用する `ReinjectionAlgorithm`。

### コンストラクタ

```
StationaryReinjection(; fallback = DataReinjection())
```
