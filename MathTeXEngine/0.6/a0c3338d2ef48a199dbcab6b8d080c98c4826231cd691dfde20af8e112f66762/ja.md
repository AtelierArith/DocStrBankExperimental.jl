```
generate_tex_elements(str)
```

LaTeX数式コードの文字列から、タプル `(texelement, position, scale)` のリストを作成します。要素の位置とスケールは、LaTeXの出力を概ね再現するように設定されています。

要素は次のいずれかのタイプです。

```
- `TeXChar` 特定のフォントを持つ（ユニコード）文字。
- `HLine` 水平線。
- `VLine` 垂直線。
```
