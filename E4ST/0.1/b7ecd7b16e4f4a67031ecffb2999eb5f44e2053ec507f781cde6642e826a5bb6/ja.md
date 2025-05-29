```
struct GenerationConstraint <: Modification
```

**世代制約** - (年間発電量) * (genテーブルの列) に基づいて制約を適用するModification。

  * `name`: 修正名
  * `col`: genテーブルの列
  * `max_values`: 年間の最大値 (最大値がない場合は空のOrderedDictがデフォルト)
  * `min_values`: 年間の最小値 (最小値がない場合は空のOrderedDictがデフォルト)
  * `gen_filters`: 発電機フィルターのOrderedDict
