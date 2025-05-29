# 関数呼び出し

```
phasor(c;origin=0.0+0.0im, ref=1, par=0,
    labelrsep=0.5, labeltsep=0.1, label="", ha="center", va="center",
    labelrelrot=false, labelrelangle=0,
    color="black", backgroundcolor="none", linesstyle="-", linewidth=1,
    width=0.2, headlength=10, headwidth=5)
```

# 説明

この関数は、始点 `origin` から終点 `origin`+`c` までのファゾールを描画します。ファゾールは、シャフトと矢印の先端から構成されています。

各ファゾール `c` は相対量としてプロットされます。すなわち、`c/ref` が実際にプロット図に表示されます。この単位ファゾールをプロットする概念は、異なる量（例えば、電圧と電流のファゾール）をプロットできるようにするために使用されます。変数 `c`、`origin`、および `ref` は同じ単位（Unitfulを通じて定義）であることが重要です。

# 変数

`c` 複素ファゾール、`origin` に対して相対的に描画される

`origin` ファゾールの原点を表す複素数。この変数は `c` と同じ単位である必要があります。

`ref` スケーリングの基準長さ。この値は、ファゾール図に電圧と電流が含まれる可能性があるため必要です。異なる電圧と電流のスケールを考慮するために、電圧ファゾールには1つの（定数の）`ref` が使用され、電流ファゾールには別の（定数の）`ref` が使用されます。この変数は `c` と同じ単位である必要があります。

`par` 平行ファゾールをプロットできるようにするために、`par` はファゾールの単位接線シフト（オフセット）を `ref` に対して指定するために使用されます。通常、`ref` は約 0.05 から 0.1 に選択されます。デフォルト値 = 0（ファゾールのシフトなし）

`labelrsep` ラベルの放射方向の単位位置（ファゾールの方向に沿って）：`labelrsep = 0` はファゾールのシャフトを表し、`labelrsep = 1` はファゾールの矢印の先端を表します。デフォルト値 = 0.5、すなわちファゾールの放射中心

`labeltsep` ラベルの接線方向の単位位置：`labeltsep = 0` はラベルがファゾールにプロットされることを意味します。`labeltsep = 0.1` は、`ref` に対して10%の変位を適用してファゾールの上にラベルをプロットします。`labeltsep = -0.2` は、`ref` に対して20%の変位を適用してファゾールの下にラベルをプロットします。デフォルト値 = 0.1

`label` ラベルの文字列；デフォルト = ""

`ha` ラベルの水平揃え；実際にはラベルの接線揃えを表します。デフォルト値 = "center"

`va` ラベルの垂直揃え；実際にはラベルの放射揃えを表します。デフォルト値 = "center"

`labelrelrot` ラベルの相対回転；`labelrelrot == false`（デフォルト値）の場合、ラベルはファゾールの方向に対して回転しません。それ以外の場合、ラベルは `labelrelangle` の角度でファゾールに対して回転します。

`labelrelangle` ファゾールの方向に対するラベルの相対角度；この角度は、`labelrelrot == true` の場合にのみ適用されます。この角度は、ファゾールの方向に対するラベルの相対的な方向を示します。デフォルト値 = 0

`color` ファゾールの色；すなわち、シャフトと矢印の先端の色；デフォルト値 = "black"

`backgroundcolor` ラベルの背景色；`labelrsep` が 0 の場合、背景色 "white" を使用できます；デフォルト値 = "none"

`linestyle` ファゾールの線スタイル；デフォルト値 = "-"

`linewidth` ファゾールの線幅；デフォルト値 = 1

`width` シャフト線の線幅；デフォルト値 = 0.2

`headlength` 矢印の先端の長さ；デフォルト値 = 10

`headwidth` 矢印の先端の幅；デフォルト値 = 5

# 例

コードをコピーして貼り付け：

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
figure(figsize=(3.3, 2.5))
rc("text", usetex=true); rc("font", family="serif")
V1 = 100V + j*0V # 電圧
Z1 = 30Ω + j*40Ω # インピーダンス
I1 = V1/Z1 # 電流
Vr = real(Z1)*I1
Vx = V1 - Vr
refV = abs(V1); refI=abs(I1)*0.8
phasor(V1, label=L"$\underline{V}_1$", labeltsep=0.1, ref=refV,
    labelrelrot=true)
phasor(Vr, label=L"$\underline{V}_r$", labeltsep=-0.25, ref=refV,
    labelrelrot=true)
phasor(Vx, origin=Vr, label=L"$\underline{V}_x$", labeltsep=-0.2, ref=refV,
    labelrelrot=true)
phasor(I1, label=L"$\underline{I}_1$", labeltsep=-0.2, labelrsep=0.7, ref=refI,
    labelrelrot=true, linestyle="--", par=-0.05)
phi1=angle(I1)
phi2=angle(V1)
angulardimension(0.3,phi1,phi2,arrowstyle1=".",arrowstyle2="-|>",ha="left",
    label=L"$\varphi_1$", labelrsep=0.05)
axis("square"); xlim(-1,1); ylim(-1,1)
removeaxes(); # 軸を削除
# save2fig("phasordiagram",crop=true);
```
