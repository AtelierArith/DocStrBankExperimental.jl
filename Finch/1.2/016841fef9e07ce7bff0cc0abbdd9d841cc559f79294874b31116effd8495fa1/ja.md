```
toeplitz(tns, dim)
```

`ToeplitzArray`を作成します。

```
    Toeplitz(tns, dim)[i...] == tns[i[1:dim-1]..., i[dim] + i[dim + 1], i[dim + 2:end]...]
```

ToplitzArrayは、元のテンソルの別の次元をシフトさせる次元を追加するものと考えることができます。
