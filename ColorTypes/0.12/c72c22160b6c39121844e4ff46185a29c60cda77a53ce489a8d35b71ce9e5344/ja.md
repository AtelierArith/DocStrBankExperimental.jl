```
reducec(op, v0, c)
reducec(op, c; [init])
```

バイナリ演算子 `op` を使用して、`c` の色チャネルを横断して減少させます。`v0` または `init` は、減少を開始するために使用される中立要素です。グレースケールの場合、

```
reducec(op, v0, c::Gray) = op(v0, comp1(c))
```

RGBの場合は、

```
reducec(op, v0, c::RGB) = op(comp3(c), op(comp2(c), op(v0, comp1(c))))
```

`c` にアルファチャネルがある場合、それは常に減少に折りたたまれる最後のものです。

!!! compat "ColorTypes 0.12"
    キーワード引数 `init` とその省略は、ColorTypes v0.12 以降が必要です。

