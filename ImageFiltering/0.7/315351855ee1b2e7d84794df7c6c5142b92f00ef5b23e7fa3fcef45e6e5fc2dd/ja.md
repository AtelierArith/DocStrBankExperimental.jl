```
findlocalmaxima(img; window=default_window(img), edges=true) -> Vector{CartesianIndex}
```

隣接するすべての要素よりも大きい値を持つ要素の座標を返します。`edges`は、各次元の最初と最後の要素を含めるかどうかを指定するブール値、または各次元のエッジ動作を別々に指定するブールのタプルです。

`default_window`は`img`の各空間次元に対して3であり、それ以外は1であるため、デフォルトでは最近接隣接要素に対して最大値が検出されます。
