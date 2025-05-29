```
constraints_list(ms::MinkowskiSum)
```

2つの多面体集合のミンコフスキー和の制約のリストを返します。

### 入力

  * `ms` – 2つの多面体集合のミンコフスキー和

### 出力

ミンコフスキー和の制約のリスト。

### アルゴリズム

`minkowski_sum`を介して具体的な集合表現を計算し、結果に対して`constraints_list`を呼び出します。
