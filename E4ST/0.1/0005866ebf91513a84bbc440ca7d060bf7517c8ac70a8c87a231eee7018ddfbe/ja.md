```
struct CapacityConstraint <: Modification
```

**キャパシティ制約** - 総容量に基づいて制約を適用する修正。

  * `name`: 修正名
  * `table`: 制約をgenまたはストレージテーブルのアイテムに適用するかどうか。
  * `max_values`: 年間の最大値（最大値がない場合は空のOrderedDictがデフォルト）
  * `min_values`: 年間の最小値（最小値がない場合は空のOrderedDictがデフォルト）
  * `table_filters`: テーブルフィルターのOrderedDict
