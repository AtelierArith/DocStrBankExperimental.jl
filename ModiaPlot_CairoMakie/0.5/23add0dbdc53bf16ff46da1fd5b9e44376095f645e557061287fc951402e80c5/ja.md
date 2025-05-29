```
showFigure(figure)
```

| プロットパッケージ  | 効果                      |
|:---------- |:----------------------- |
| GLMakie    | 単一ウィンドウに`figure`を表示します。 |
| WGLMakie   | 単一ウィンドウに`figure`を表示します。 |
| CairoMakie | 呼び出しは無視されます             |
| PyPlot     | 呼び出しは無視されます             |
| NoPlot     | 呼び出しは無視されます             |

# 例

```julia
import ModiaResult
ModiaResult.@usingModiaPlot
...
plot(..., figure=1)
plot(..., figure=2)
plot(..., figure=3)

showFigure(2)
showFigure(1)
```
