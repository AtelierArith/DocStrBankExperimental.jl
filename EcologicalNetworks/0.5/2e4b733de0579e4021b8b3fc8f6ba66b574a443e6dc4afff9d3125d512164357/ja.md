```
conditional_entropy(P::AbstractArray, given::I)
```

確率行列の条件付きエントロピーを計算します。`given = 1` の場合、列のエントロピーであり、`given = 2` の場合はその逆です。出力はビット単位です。

`P` が有効な確率行列であるかどうかはチェックしません。
