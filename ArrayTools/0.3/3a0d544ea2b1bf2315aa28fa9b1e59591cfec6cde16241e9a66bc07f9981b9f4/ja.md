```
split_interval(I, J, +/-, k) -> Ia, Ib, Ic
```

単位範囲 `I` と `J` およびオフセット `±k` が与えられたとき、3つの単位範囲を生成し、`Ia ∪ Ib ∪ Ic = I` となるようにします：

  * `∀ i ∈ Ia`、`i ± k < first(J)`；
  * `∀ i ∈ Ib`、`i ± k ∈ J`；
  * `∀ i ∈ Ic`、`i ± k > last(J)`。

単位範囲はその最初と最後の値で置き換えることができます：

```
split_interval(first(I), last(I), first(J), last(J), +/-, k)
```

は上記と同じ結果を生成します。
