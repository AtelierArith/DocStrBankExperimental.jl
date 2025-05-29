equalisecolourmap - カラーマップの色のコントラストを均一化する equalizecolormap

```
Usage: newrgbmap = equalisecolourmap(rgblab, map, formula, W, sigma, diagnostics)
                   equalizecolormap(....

Arguments:     rgblab - "RGB" または "LAB" の文字列で、マップ内のデータのタイプを示します。
                  map - Nx3 RGB または CIELAB カラーマップ
                        または ColorTypes.RGB{Float64} 値の配列
              formula - "CIE76" または "CIEDE2000" の文字列
                    W - 明度、クロマ、色相成分に適用される重みの3ベクトル。
                        明度のみを考慮するには [1, 0, 0] を使用することをお勧めします。
                        必要に応じて、完全な式のために [1, 1, 1] を使用します。
                sigma - オプションのガウス平滑化パラメータ。
               cyclic - カラーマップが循環しているかどうかを示すブールフラグ。
                        これは、端点での平滑化の適用方法に影響します。
          diagnostics - 診断プロットを表示するかどうかを示すオプションのブールフラグ。
                        デフォルトは false です。

Returns:    newrgbmap - カラーマップに沿った色の知覚的コントラストが一定になるように調整された RGB カラーマップ。
                        これは Nx3 の Float64 値の配列です。

完全なドキュメントについては equalisecolourmap() を参照してください。
                                 ^     ^
```

See also: cmap, sineramp, circlesineramp
