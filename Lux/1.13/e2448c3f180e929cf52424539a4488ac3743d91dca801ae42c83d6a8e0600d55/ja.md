```
AdaptiveMaxPool(output_size)
```

適応的最大プーリング層。出力が `size(y)[1:N] == output_size` となるように必要なウィンドウサイズを計算します。

## 引数

  * `output_size`: 出力の最初の `N` 次元のサイズ

## 入力

  * `x`: 入力として `ndims(x) == N + 2` の配列を期待します。すなわち、`N` の特徴次元の後にチャネルとバッチ次元が続きます。ここで、`N = length(output_size)` です。

## 戻り値

  * サイズ `(out..., C, N)` の出力
  * 空の `NamedTuple()`
