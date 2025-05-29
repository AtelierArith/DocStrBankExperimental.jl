# 関数呼び出し

```
arrowaxes(fig=gcf(), ax=gca(); xmin, xmax, ymin, ymax,
    xa=0, ya=0, xlabel="", ylabel="",
    xneg = false, yneg = false,
    color="black", backgroundcolor="none", axisoverhang = 0.18,
    linewidth = 0.75, headwidth = 0.06, headlength = 0.09, overhang = 0.1,
    labelsep = 0.06, left=0.2, right=0.85, bottom=0.20, top=0.85)
```

# 説明

フレームの代わりに水平軸と垂直軸を持つプロットを作成します。

# 変数

`fig` 図のハンドル; デフォルトでは、実際の図のハンドルが使用されます

`xmin` 水平軸の最小値; デフォルト値 = 実際のスケーリング

`xmax` 水平軸の最大値; デフォルト値 = 実際のスケーリング

`ymin` 垂直軸の最小値; デフォルト値 = 実際のスケーリング

`ymax` 垂直軸の最大値; デフォルト値 = 実際のスケーリング

`ax` 軸のハンドル; デフォルトでは、実際の図の軸のハンドルが使用されます

`xa` 垂直軸の水平位置; デフォルト値 = 0

`ya` 水平軸の垂直位置; デフォルト値 = 0

`xlabel` x軸のラベル; デフォルト値 = ""

`ylabel` y軸のラベル; デフォルト値 = ""

`xneg` trueの場合、水平矢印は右から左に描画されます; デフォルト値 = `false`

`yneg` trueの場合、垂直矢印は上から下に描画されます; デフォルト値 = `false`

`color` 軸の色; デフォルト値 = "black"

`backgroundcolor` ラベルの背景色; labelrsepが0の場合、背景色"white"を使用できます; デフォルト値 = "none"

`axisoverhang` プロット領域に対する軸のオーバーハング; デフォルト値 = 0.18 (プロット幅の18%)

`linewidth` 軸の線幅; デフォルト値 = 0.75

`headwidth` プロット領域に対するヘッドの幅; デフォルト値 = 0.045 (水平プロット幅の4.5%)

`headlength` プロット領域に対するヘッドの長さ; デフォルト値 = 0.07 (水平プロット幅の7%)

`overhang` 矢印のヘッドのオーバーハング; デフォルト値 = 0.0

`labelsep` 軸からラベルの位置、プロット領域に対する相対位置; デフォルト値 = 0.05 (プロット幅の5%)

`left` 図の左側; デフォルト値 = 0.2

`right` 図の右側; デフォルト値 = 0.85

`bottom` 図の下側; デフォルト値 = 0.2

`top` 図の上側; デフォルト値 = 0.85

`yleft` trueの場合、y軸の左にylabelを配置

`xbelow` trueの場合、x軸の下にxlabelを配置

# 例

以下のコードをコピーして貼り付けてください:

```julia
using Unitful,Unitful.DefaultSymbols,ElectricalEngineering,PyPlot
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
x=collect(0.0:0.1:5.0); y=exp.(sin.(x));
plot(x,y,color=colorBlack1, linewidth=lineWidth1, linestyle=lineStyle1)
xlim(0,5); ylim(0,3); arrowaxes(xlabel=L"$x$",ylabel=L"$y$")
# save2fig("arrowaxes", crop=true)
```
