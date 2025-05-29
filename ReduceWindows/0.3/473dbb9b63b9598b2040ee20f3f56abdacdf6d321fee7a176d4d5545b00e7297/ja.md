```
reduce_window(f, arr, window)
```

`arr`の上にスライディングウィンドウを移動させ、`reduce(f, view(arr, shifted window...))`を適用します。例えば、`window = (-1:2, 3:4)`は次のような出力行列を生成します：

`out[i,j] = reduce(f, arr[(i-1):(i+2), (j+3):(j+4)])`

この式は意味的には正しいですが、実装でははるかに少ない作業が行われます。時間計算量は`O(log(k) * n)`であり、ここで

  * `n`は配列のサイズ：`n = length(arr)`
  * `k`はウィンドウのサイズ：`k = prod(length, window)`

`reduce_window`は、`f`が結合的かつ可換的であると仮定しています。
