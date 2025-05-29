```
manhattan_distance(a, b, model::ABM)
```

`a`と`b`（エージェントまたはエージェントの位置のいずれか）間のマンハッタン距離を返します。周期境界条件を尊重します（使用している場合）。現在、`AbstractGridSpace`および`ContinuousSpace`のように、意味のある任意の空間で機能します。
