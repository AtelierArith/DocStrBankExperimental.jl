```
softmax1(x, dims = 1)
```

softmaxのように動作しますが、dimsに沿ってゼロの追加ロジットがあるかのように動作します（これは出力から除外されます）。したがって、値は0と1の間の値に合計されます。

詳細はhttps://www.evanmiller.org/attention-is-off-by-one.htmlを参照してください。
