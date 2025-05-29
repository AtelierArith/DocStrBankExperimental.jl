```
recurrenceplot([io,] R; minh = 25, maxh = 0.5, ascii, kwargs...) -> u
```

再帰行列 `R` のテキストベースの散布図表現を `io`（デフォルトは `stdout`）に表示するために `UnicodePlots` を使用します。行列は最小 `minh` 行、最大 `maxh*displaysize(io)[1]`（すなわちデフォルトでは表示の半分）を占めます。常に等しいアスペクト比でプロットしようとするため、プロットの幅がさらに小さい場合、最小の高さは幅によって決まります。

キーワード `ascii::Bool` は、プロットのすべての要素がASCII文字（`true`）またはUnicode（`false`）であることを保証できます。

残りの `kwargs` は `UnicodePlots.scatterplot` に渡されます。

この関数の精度は、行列のサイズが表示の幅と高さよりも大幅に大きい場合（行列の各インデックスが1文字であると仮定）に急激に低下することに注意してください。
