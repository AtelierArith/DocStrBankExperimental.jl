```
save(term, output, [termopts,] [font,] [size,] [linewidth,] [background,] [handle]) -> nothing
```

現在の図（または `handle` で指定された図）を指定された `term` を使用して保存します。オプションで、フォント、サイズ、線幅、および背景を引数として指定できます。

任意の gnuplot コマンドが送信された場合は `true` を返し、そうでない場合は `false` を返します。
