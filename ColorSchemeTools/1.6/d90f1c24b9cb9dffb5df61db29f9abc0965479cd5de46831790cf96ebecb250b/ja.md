```
extract_weighted_colors(imfile, n=10, i=10, tolerance=0.01; shrink = 2)
```

画像ファイル内の色のクラスタの色と重みを抽出します。ColorSchemeと重みを返します。

例:

```
pal, wts = extract_weighted_colors(imfile, n, i, tolerance; shrink = 2)
```
