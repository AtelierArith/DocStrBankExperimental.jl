```
getplotdata(tess, quadrants, phasediffs, g2f)
```

すべてのタイルのエッジの複素座標と、その位相四分円を指定する対応するインデックスを持つベクトルを返します。

この関数は、`PlotData()`引数を使用して`grpf`を呼び出した結果を使用して最終的なタイルをプロットするのに便利です。

エッジの色は（Qは「四分円」を意味します）：

| 色インデックス |    意味    |       四分円位相       |
|:-------:|:--------:|:-----------------:|
|    1    |   Q 1    |  0 ≤ arg f < π/2  |
|    2    |   Q 2    |  π/2 ≤ arg f < π  |
|    3    |   Q 3    | π ≤ arg f < 3π/2  |
|    4    |   Q 4    | 3π/2 ≤ arg f < 2π |
|    5    | 位相変化（境界） |         -         |
|    6    |  候補エッジ   |         -         |

# 例

自己完結型ではありませんが、この例は`getplotdata`がどのように使用できるかを示しています：

```julia
roots, poles, quads, phasediffs, tess, g2f = grpf(f, origcoords, PlotData());
z, edgecolors = getplotdata(tess, quadrants, phasediffs, g2f);

using Plots
plot(real(z), imag(z), group=edgecolors)
```
