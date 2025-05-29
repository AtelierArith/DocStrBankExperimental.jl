```
reduce_full(A::SMat{ZZRingElem}, g::SRow{ZZRingElem},
                      with_transform = Val(false)) -> SRow{ZZRingElem}, Vector{Int}
```

$$
g
$$

を$A$で剰余計算し、$A$が上三角行列であると仮定します。

2つ目の返り値は、変化した$A$のピボット要素の配列です。

`with_transform`が`Val(true)`に設定されている場合、追加で変換の配列が返されます。
