```
struct RampBi <: AbstractRampParameters
```

ノードの正および負のランピング制約のためのパラメータ。

# フィールド

  * **`up::TimeProfile`** はノードの最大正変化率です。
  * **`down::TimeProfile`** はノードの最大負変化率です。

!!! note
    単一の `TimeProfile` を入力として提供した場合、正および負の境界に同じプロファイルが使用されます。

