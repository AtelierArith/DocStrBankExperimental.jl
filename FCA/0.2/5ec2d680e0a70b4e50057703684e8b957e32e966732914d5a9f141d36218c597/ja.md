```
free_whiten(Z; mat = "her")
```

この関数は、自由確率の意味で入力行列の配列をホワイトニングします。

# 引数

  * `Z`: 同じ次元の行列の配列
  * `mat`: Z[i]のタイプ、有効なオプションは "her" と "rec" です

# 出力

  * `Y`: 自由確率の意味でホワイトニングされた中心化された行列の配列、すなわち、Tr(Y[i]*Y[j]')/size(Y[1],1) = (i == j)
  * `U`: サイズs-by-sの行列、ここでs = size(Z, 1)
  * `Σ`: サイズs-by-sの行列、
