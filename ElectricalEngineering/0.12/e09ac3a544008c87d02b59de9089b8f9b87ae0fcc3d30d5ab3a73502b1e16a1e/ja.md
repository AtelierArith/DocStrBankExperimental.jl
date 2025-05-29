# 関数呼び出し

```
lengthdimension(x1=0, y1=0, x2=1, y2=1;
    label = "", labeltsep = 0.1, labelrsep=0.5, labelrelrot=false,
    labelrelangle=0, ha = "center", va = "center",
    color="black", backgroundcolor = "none",
    arrowstyle1 = "<|-", arrowstyle2 = "-|>", linewidth=0.6, linestyle = "-",
    width=0.2, headlength=5, headwidth=2.5,
    par=0, paroverhang = 0.02, parcolor = "black",
    parlinewidth=0.6, parlinestyle = "-")

```

# 説明

この関数は、矩形のxおよびy座標に基づいてラベル付きの長さ寸法を描画します。長さ寸法の矢印は、単一のパラメータ`par`を使用して指定された座標に平行にシフトできます。さらに、指定された座標から長さ寸法への補助線が描画されます。

# 変数

`x1` 長さ寸法の始点のx成分; デフォルト値 = 0

`y1` 長さ寸法の始点のy成分; デフォルト値 = 0

`x2` 長さ寸法の終点のx成分; デフォルト値 = 1

`y2` 長さ寸法の終点のy成分; デフォルト値 = 1

`label` 角度のラベル; デフォルト値 = ""

`labeltsep` ラベルの接線方向の単位位置: `labeltsep = 0`はラベルが位相器上にプロットされることを意味します; `labeltsep = 0.1`はラベルを位相器の上にプロットし、`ref`に対して10%の変位を適用します; `labeltsep = -0.2`はラベルを位相器の下にプロットし、`ref`に対して20%の変位を適用します; デフォルト値 = 0.1

`labelrsep` ラベルの半径方向の単位位置（位相器の方向）: `labelrsep = 0`は位相器のシャフトを表し、`labelrsep = 1`は位相器の矢印の先端を表します; デフォルト値 = 0.5、すなわち位相器の半径中心

`labelrelrot` ラベルの相対回転; `labelrelrot == false`（デフォルト値）の場合、ラベルは弧の中心に対して回転しません; それ以外の場合、ラベルは角度`labelrelangle`に対して回転します

`labelrelangle` 弧の中心に対するラベルの相対角度; この角度は`labelrelrot == true`の場合にのみ適用されます; この角度は弧の中心に対するラベルの相対的な向きを示します; デフォルト値 = 0

`ha` ラベルの水平揃え; 実際にはラベルの半径方向の揃えを表します; デフォルト値 = "center"

`va` ラベルの垂直揃え; 実際にはラベルの接線方向の揃えを表します; デフォルト値 = "center"

`color` 弧の色; デフォルト値 = "black"

`textcolor` ラベルの色; デフォルト値 = `color`

`backgroundcolor` ラベルの背景色; labelrsepが0の場合、背景色"white"を使用できます; デフォルト値 = "none"

`arrowstyle1` 線の始点の矢印スタイル; デフォルト値 = "<|-"; 有効な文字列は:

  * `.` ドットマーカー
  * `<|-` 矢印

`arrowstyle2` 線の終点の矢印スタイル; デフォルト値 = "-|>"; 有効な文字列は:

  * `.` ドットマーカー
  * `-|>` 矢印

`headlength` 矢印の先端の長さ; デフォルト値 = 5

`headwidth` 矢印の先端の幅; デフォルト値 = 2.5

`par` 指定された座標`x1`, `y1`, `x2`, `y2`に平行に長さ寸法を描画するために、`par`は長さ寸法の単位接線シフト（オフセット）を指定するために使用されます; デフォルト値 = 0（シフトなし）

`paroverhang` `par != 0`の場合に描画される補助線は、絶対的なオーバーハング`paroverhang`を示します; デフォルト値 = 0.02

`parcolor` 補助線の色; デフォルト値 = "black"

`parlinewidth` 補助線の線幅; デフォルト値 = 0.6

`parlinestyle` 補助線の線スタイル; デフォルト値 = "-"

# 例

コードをコピーして貼り付けます:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
t1=0.2;t2=0.3;ymax=1
t=[0,t1,t1+t2,2*t1+t2,2*(t1+t2),3*t1+2*t2]
y=[0,ymax,0,ymax,0,ymax]
step(t,y,linewidth=1,color="black")
grid(true); xlim(0,1), ylim(-0.1,1.3);
xlabel(L"$t$\,(s)"); ylabel(L"$y$")
lengthdimension(0,0.2,t1,0.2,label=L"$t_1$",labeltsep=0,backgroundcolor="white")
lengthdimension(t1,0.2,t1+t2,0.2,label=L"$t_2$",labeltsep=0,backgroundcolor="white")
lengthdimension(t1,ymax,2*t1+t2,ymax,label=L"$T$",par=0.1,labeltsep=0.05,labelrsep=0.7)
# save2fig("lengthdimension",crop=true)
```
