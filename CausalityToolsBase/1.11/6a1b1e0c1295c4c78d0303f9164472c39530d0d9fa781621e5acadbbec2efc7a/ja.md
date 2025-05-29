```
optimal_dimension(v; dims = 2:8,
    method_dimension = "fnn", method_delay = "first_min")
```

`v`の最適埋め込み次元を推定するために、まず最適遅延を推定し、その遅延を使用して次元を推定します。

## 引数

  * **`v`**: 埋め込み次元を推定するデータ系列。
  * **`dims`**: 試す次元
