```
saveFigure(figure, file; kwargs...)
```

ファイルに図を保存します。ファイル拡張子が画像形式を定義します（例えば `*.png`）。

| プロットパッケージ  | サポートされているファイル拡張子                                                                                                      |
|:---------- |:--------------------------------------------------------------------------------------------------------------------- |
| GLMakie    | png, jpg, bmp                                                                                                         |
| WGLMakie   | png                                                                                                                   |
| CairoMakie | png, pdf, svg, eps                                                                                                    |
| PyPlot     | [backend](https://matplotlib.org/stable/tutorials/introductory/usage.html) に依存します (png, pdf, jpg, tiff, svg, ps, eps) |
| NoPlot     | 呼び出しは無視されます                                                                                                           |

# キーワード引数

  * resolution: (width::Int, height::Int) のシーンの寸法なし単位（GLMakie と WGLMakie の px に相当）。

# 例

```julia
import ModiaResult
ModiaResult.@usingModiaPlot
...

plot(..., figure=1)
plot(..., figure=2)

saveFigure(1, "plot.png")   # png形式で保存
saveFigure(2, "plot.svg")   # svg形式で保存
```
