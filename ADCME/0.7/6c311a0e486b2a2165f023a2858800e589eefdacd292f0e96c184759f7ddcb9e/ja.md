```
softmax_cross_entropy_with_logits(logits::Union{Array, PyObject}, labels::Union{Array, PyObject})
```

`logits` と `labels` の間のソフトマックス交差エントロピーを計算します。

`logits` は通常、線形層の出力です。例えば、

```
logits = [
    0.124575  0.511463   0.945934
    0.538054  0.0749339  0.187802
    0.355604  0.052569   0.177009
    0.896386  0.546113   0.456832
]
labels = [2;1;2;3]
```

!!! info
    `labels` の値は {1,2,...,`num_classes`} からのものです。ここで `num_classes` は `logits` の列の数です。


`logits` に関連付けられた予測ラベルは 

```
argmax(softmax(logits), dims = 2)
```

ラベルはワンホットベクトルでも表現できます。

```
labels = [0 1
          1 0
          0 1
          0 1]
```
