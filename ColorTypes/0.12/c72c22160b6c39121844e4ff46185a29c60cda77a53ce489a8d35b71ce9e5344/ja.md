```
reducec(op, v0, c)
reducec(op, c; [init])
```

カラー チャンネル `c` に対して二項演算子 `op` を使って縮約します。`v0` または `init` は縮約を開始するために使用される中立要素です。グレースケールの場合、

```
reducec(op, v0, c::Gray) = op(v0, comp1(c))
```

RGB の場合は、

```
reducec(op, v0, c::RGB) = op(comp3(c), op(comp2(c), op(v0, comp1(c))))
```

`c` にアルファ チャンネルがある場合、それは常に縮約に折りたたまれる最後のものです。

!!! compat "ColorTypes 0.12"
    キーワード引数 `init` とその省略は、ColorTypes v0.12 以降が必要です。

