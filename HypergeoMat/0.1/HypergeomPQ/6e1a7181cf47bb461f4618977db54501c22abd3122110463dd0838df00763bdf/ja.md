```
hypergeomPQ(m, a, b, X[, alpha])
```

行列引数の切断された超幾何関数を計算します。超幾何関数は通常、対称実行列またはエルミート複素行列に対して定義されますが、任意の正方行列が許可されます。

# 引数

  * `m`: 和の切断重み、正の整数
  * `a`: "上"のパラメータ、実数または複素数のベクトル、空である可能性があります
  * `b`: "下"のパラメータ、実数または複素数のベクトル、空である可能性があります
  * `X`: 正方行列、実数または複素数
  * `alpha`: アルファパラメータ、正の数; 省略された場合、`alpha=2`が使用されます
