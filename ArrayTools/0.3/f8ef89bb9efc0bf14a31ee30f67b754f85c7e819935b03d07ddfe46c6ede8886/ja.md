```
axis_limits(I) = (i0,i1)
```

は、インデックス範囲 `I` の限界 `i0` と `i1` を `Int` の2タプルとして返し、`i0:i1` が `I` と同じインデックスを表すようにします（ただし、`step(I) < 0` の場合は同じ順序ではありません）。`step(I)` が ±1 と等しくない場合、`ArgumentError` 例外がスローされます。
