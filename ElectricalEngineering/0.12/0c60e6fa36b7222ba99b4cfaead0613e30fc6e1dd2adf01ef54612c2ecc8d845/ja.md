# 関数呼び出し

```
phasordimension(c; origin = 0im, ref = 1;
    label = "", labeltsep = 0.1, labelrsep=0.5, labelrelrot=false,
    labelrelangle=0, ha = "center", va = "center",
    color="black", backgroundcolor = "none",
    arrowstyle1 = "<|-", arrowstyle2 = "-|>", linewidth=0.6, linestyle = "-",
    width=0.2, headlength=5, headwidth=2.5,
    par=0, paroverhang = 0.02, parcolor = "black",
    parlinewidth=0.6, parlinestyle = "-")

```

# 説明

この関数は、長さの次元を矩形のxおよびy座標に基づいてラベル付きで描画します。長さの次元矢印は、単一のパラメータ`par`を使用して指定された座標に平行にシフトできます。さらに、指定された座標から長さの次元への補助線が描画されます。

# 変数

`c` 次元を持つ複素数ファゾール

`origin` ファゾール次元の原点を表す複素数; この変数は`c`と同じ単位である必要があります

`ref` スケーリングの基準長さ; ファゾール図には電圧と電流が含まれる可能性があるため、異なる電圧と電流のスケールを考慮するために、電圧ファゾール用の1つの（定数の）`ref`と電流ファゾール用の別の（定数の）`ref`が使用されます; この変数は`c`と同じ単位である必要があります

`label` 角度のラベル; デフォルト値 = ""

`labelphisep` 弧に対するラベルの角度の分離; `labelphisep == 0`の場合、ラベルは角度`phi1`に位置し、`labelphisep == 1`の場合、ラベルは角度`phi2`に位置します; デフォルト値 = 0.5、`phi1`と`phi2`の間の真ん中

`labelrsep` ラベルの放射方向の位置（ファゾールの方向に対して）:`labelrsep = 0`はラベルを弧の上に配置します。正の値はラベルを弧の外側に配置し、負の値はラベルを弧の内側に配置します; デフォルト値 = 0.1

`labelrelrot` ラベルの相対回転; `labelrelrot == false`（デフォルト値）の場合、ラベルは弧の中心に対して回転しません; それ以外の場合、ラベルは角度`labelrelangle`に対して回転します

`labelrelangle` 弧の中心に対するラベルの相対角度; この角度は`labelrelrot == true`の場合にのみ適用されます; この角度は、弧の中心に対するラベルの相対的な向きを示します; デフォルト値 = 0

`ha` ラベルの水平揃え; 実際にはラベルの放射方向の揃えを表します; デフォルト値 = "center"

`va` ラベルの垂直揃え; 実際にはラベルの接線方向の揃えを表します; デフォルト値 = "center"

`color` 弧の色; デフォルト値 = "black"

`textcolor` ラベルの色; デフォルト値 = `color`

`backgroundcolor` ラベルの背景色; labelrsepが0の場合、背景色"white"を使用できます; デフォルト値 = "none"

`arrowstyle1` 弧の始まりの矢印スタイル; デフォルト値 = "."; 有効な文字列は:

  * `.` ドットマーカー
  * `<|-` 矢印

`arrowstyle2` 弧の終わりの矢印スタイル; デフォルト値 = "-|>"; 有効な文字列は:

  * `.` ドットマーカー
  * `-|>` 矢印

`headlength` 矢印の頭の長さ; デフォルト値 = 5

`headwidth` 矢印の頭の幅; デフォルト値 = 2.5

`par` 指定された座標`x1`、`y1`、`x2`、`y2`に平行に長さの次元を描画できるようにするために、`par`は長さの次元の単位接線シフト（オフセット）を指定するために使用されます; デフォルト値 = 0（シフトなし）

`paroverhang` `par != 0`の場合に描画される補助線は、絶対的なオーバーハング`paroverhang`を示します; デフォルト値 = 0.02

`parcolor` 補助線の色; デフォルト値 = "black"

`parlinewidth` 補助線の線幅; デフォルト値 = 0.6

`parlinestyle` 補助線の線スタイル; デフォルト値 = "-"

# 例

以下のコードをコピーして貼り付けてください:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
Z1 = pol(1,30°)
phasor(Z1, label=L"$\underline{Z}$", labeltsep = 0.05, labelrelrot=true)
phasordimension(real(Z1), label=L"$R$", arrowstyle1="",
    linestyle="-", linewidth=1, headwidth=5, headlength=10,
    labeltsep=0, color="gray", backgroundcolor="white")
    phasordimension(j*imag(Z1), origin=real(Z1), label=L"j$\cdot X$",
    arrowstyle1="", linestyle="-", linewidth=1, headwidth=5, headlength=10,
    labeltsep=0, color="gray", backgroundcolor="white")
arrowaxes(xmin = real(Z1)+0.1, xlabel="Re", ylabel=L"j$\cdot$Im")
xlim([-0.5,1]);ylim([-0.5,1]); axis("square"); removeaxes();
# save2fig("phasordimension", crop=true)
```
