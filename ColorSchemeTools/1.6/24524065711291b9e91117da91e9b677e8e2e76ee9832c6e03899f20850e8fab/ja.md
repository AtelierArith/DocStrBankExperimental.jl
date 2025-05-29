```
colorscheme_weighted(colorscheme, weights, length)
```

指定された `length`（デフォルトは50）の新しい ColorScheme を返します。ここで、`colorscheme` の各色の割合は、各エントリの関連する重みで表されます。

例:

```
colorscheme_weighted(extract_weighted_colors("hokusai.jpg")...)
colorscheme_weighted(extract_weighted_colors("filename00000001.jpg")..., 500)
```
