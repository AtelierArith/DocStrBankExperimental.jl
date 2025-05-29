```
mapreducec(f, op, v0, c)
mapreducec(f, op, c; [init])
```

カラー チャンネル `c` に対してバイナリ演算子 `op` を使用して削減を行い、最初に各チャンネルに `f` を適用します。`v0` または `init` は、削減を開始するために使用される中立要素です。グレースケールの場合、

```
mapreducec(f, op, v0, c::Gray) = op(v0, f(comp1(c)))
```

一方、RGBの場合は

```
mapreducec(f, op, v0, c::RGB) = op(f(comp3(c)), op(f(comp2(c)), op(v0, f(comp1(c)))))
```

`c` にアルファ チャンネルがある場合、それは常に削減に折りたたまれる最後のチャンネルです。

!!! compat "ColorTypes 0.12"
    キーワード引数 `init` とその省略は、ColorTypes v0.12 以降が必要です。

