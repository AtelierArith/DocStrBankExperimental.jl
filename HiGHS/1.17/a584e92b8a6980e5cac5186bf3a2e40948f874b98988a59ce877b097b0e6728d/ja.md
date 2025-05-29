```
Highs_getDualUnboundednessDirection(highs, has_dual_unboundedness_direction, dual_unboundedness_direction_value)
```

双対無限大方向（原始非可行性の証明に対応する）を持つかどうかを示し、存在しない場合はLPを解く代償としてそれを取得します（dual*unboundedness*directionがnullptrでない場合）。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `has_dual_unboundedness_direction`: 双対無限大方向が存在する場合は1を格納するintへのポインタ。
  * `dual_unboundedness_direction_value`: 無限大方向で満たされた長さ[num_col]の配列。
