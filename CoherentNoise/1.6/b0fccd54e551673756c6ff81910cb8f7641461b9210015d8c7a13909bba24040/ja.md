```
cache(x::AbstractSampler)
```

入力座標のセットとその対応する出力値をソースサンプラーからキャッシュする修飾子サンプラーを構築します。入力座標が以前にキャッシュされた出力と異なる場合、キャッシュは無効化され、新しい出力がキャッシュされます。

キャッシングは、サンプラーが複数の修飾子のソースとして使用される場合に便利です。キャッシングがないと、重複した入力ソースが同じ出力を冗長に計算することになり、特に長いパイプラインが長いサブグラフを共有する場合には高コストになります。
