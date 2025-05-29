```
mapreducec(f, op, v0, c)
```

カラー チャンネル `c` に対してバイナリ演算子 `op` を使用して還元を行い、最初に各チャンネルに `f` を適用します。`v0` は還元を開始するために使用される中立要素です。グレースケールの場合、

```
mapreducec(f, op, v0, c::Gray) = op(v0, f(comp1(c)))
```

RGB の場合は

```
mapreducec(f, op, v0, c::RGB) = op(f(comp3(c)), op(f(comp2(c)), op(v0, f(comp1(c)))))
```

`c` にアルファ チャンネルがある場合、それは常に還元に折りたたまれる最後のものです。
