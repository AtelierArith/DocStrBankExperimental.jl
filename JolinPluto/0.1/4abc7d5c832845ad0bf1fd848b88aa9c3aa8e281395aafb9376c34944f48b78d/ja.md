```julia
viewof(:symbol, element)
viewof("symbol", element)
```

HTML `element`を返し、その最新のJavaScript値を`symbol`の定義として使用します。

# 例

```julia
viewof(:x, html"<input type=range>")
```

別のセルでは：

```julia
x^2
```

最初のセルは、0から100までの範囲のスライダーをセルの出力として表示します。2番目のセルは`x`の平方を表示し、スライダーが動かされるとリアルタイムで更新されます。
