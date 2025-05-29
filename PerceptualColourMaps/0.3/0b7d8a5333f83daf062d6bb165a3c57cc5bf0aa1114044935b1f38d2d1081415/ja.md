linearrgbmap: 指定された色への黒からの線形RGBカラーマップ

```
Usage: cmap = linearrgbmap(C, N)

Arguments:  C - 3ベクトルでRGB色を指定
            N - カラーマップ要素の数、デフォルトは256

Returns: cmap - [0 0 0]からRGB色CまでのN要素のColorTypes.RGBAカラーマップ
```

結果として得られたカラーマップをequalisecolourmap()に渡して、知覚的な明るさで均一なステップを持つマップを取得することをお勧めします。

```
> cmap = equalisecolourmap("rgb", linearrgbmap(C, N))
```

関連項目: equalisecolourmap, ternarymaps
