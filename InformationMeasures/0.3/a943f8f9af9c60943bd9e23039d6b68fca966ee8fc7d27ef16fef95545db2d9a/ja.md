```
discretize_values(values_x; <keyword arguments>)
```

連続測定値を離散ビンに割り当てます。

# 引数

  * `values_x`: データ値。
  * `mode="uniform_width"`: 離散化アルゴリズム。
  * `number_of_bins=0`: ビンの数（`mode`が`"bayesian_blocks"`の場合は上書きされます）。
  * `get_number_of_bins=get_root_n`: ビンの数を計算するためのメソッド（`number_of_bins`が`0`の場合のみ呼び出されます）。
