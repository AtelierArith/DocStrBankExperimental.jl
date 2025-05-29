`TransparentColor{C,T,N}` は、透明度を持つ任意の色の抽象型です。`C` パラメータは、純色（透明度なし）の型を指し、`color_type` を使って抽出できます。`T` は `C` と `alpha` チャンネルの両方の要素型であり、`N` は `Colorant` と同じ意味を持ち（対応する色型よりも1大きい）、透明度の情報を持ちます。

すべての透明型は、2つの構築モードをサポートする必要があります：

```
P(color, alpha)
P(component1, component2, component3, alpha) （3成分の色を仮定）
```

`Colorant` `c` に対して、色成分は `color(c)` で抽出でき、アルファチャンネルは `alpha(c)` で抽出できます。`ARGB32` のような型には `alpha` という名前のフィールドがないことに注意してください。

`RGB` のようなほとんどの具体的な型は、`ARGB` と `RGBA` の透明なアナログを持っています。これら2つは異なる内部ストレージ順序を示します（`AlphaColor` と `ColorAlpha`、および `alphacolor` と `coloralpha` 関数を参照）。
