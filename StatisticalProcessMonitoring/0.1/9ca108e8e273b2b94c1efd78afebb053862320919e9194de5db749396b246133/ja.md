```
optimize_limit(CH::ControlChart, solver = :Bootstrap; hmax = 20.0, kw...)
```

ControlChartオブジェクトの管理限界を最適化します。

### 引数

  * `CH::ControlChart`: 最適化するControlChartオブジェクト。
  * `solver::Symbol`: 使用するソルバーアルゴリズム（デフォルト: `:Bootstrap`）。

### キーワード引数

  * `hmax::Float64`: 管理限界の最大値。二分法アルゴリズムでのみ使用されます（デフォルト: 100.0）
  * `kw...`: アルゴリズムに渡す追加のキーワード引数。

### 戻り値

```
最適化された管理限界の値。
```

### 発生する例外

```
ValueError: 設定で指定された最適化方法が不明な場合。
```
