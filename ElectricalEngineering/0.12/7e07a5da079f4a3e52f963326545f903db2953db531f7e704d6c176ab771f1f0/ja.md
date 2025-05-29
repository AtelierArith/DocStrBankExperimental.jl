# 関数呼び出し

```
angulardimension(r = 1, phi1 = 0, phi2 = pi/2; origin = 0.0im,
    label= "", labelphisep = 0.5, labelrsep = 0.1,
    labelrelrot = false, labelrelangle = 0, ha = "center", va = "center",
    color="black", backgroundcolor="none",
    arrowstyle1 = ".", arrowstyle2 = "-|>", dot90 = false,
    linewidth = 0.6, linestyle = "-", width = 0.2,
    headlength = 5, headwidth = 2.5)
```

# 説明

この関数は、位相間の角度をラベル付けするために意図された矢印付きの弧を描画します。弧は角度 `phi1`（開始）から `phi2`（終了）まで描かれます。開始と終了の矢印の形状を設定できます。弧にはラベルを付けることができ、オプションで直角（90°）を示すためにドットマーカーを使用できます。

# 変数

`r` 単位のない弧の半径; 0と1の間でなければならない; デフォルト値 = 1

`phi1` 弧の開始の位相角; デフォルト値 = 0

`phi2` 弧の終了の位相角; デフォルト値 = pi/2

`origin` 単位のない弧の原点を示す複素数; デフォルト値 = 0.0 + 0.0im

`label` 角度のラベル; デフォルト値 = ""

`labelphisep` 弧に対するラベルの角度の分離; `labelphisep == 0` の場合、ラベルは角度 `phi1` に位置し、`labelphisep == 1` の場合、ラベルは角度 `phi2` に位置します; デフォルト値 = 0.5、`phi1` と `phi2` の間の真ん中

`labelrsep` ラベルの放射方向の位置（位相の方向）: `labelrsep = 0` はラベルを弧の上に配置します。正の値はラベルを弧の外側に配置し、負の値はラベルを弧の内側に配置します; デフォルト値 = 0.1

`labelrelrot` ラベルの相対回転; `labelrelrot == false`（デフォルト値）の場合、ラベルは弧の中心に対して回転しません; それ以外の場合、ラベルは角度 `labelrelangle` に対して回転します

`labelrelangle` 弧の中心に対するラベルの相対角度; この角度は、`labelrelrot == true` の場合のみ適用されます; この角度は、弧の中心に対するラベルの相対的な向きを示します; デフォルト値 = 0

`ha` ラベルの水平方向の整列; 実際にはラベルの放射方向の整列を表します; デフォルト値 = "center"

`va` ラベルの垂直方向の整列; 実際にはラベルの接線方向の整列を表します; デフォルト値 = "center"

`color` 弧の色; デフォルト値 = "black"

`textcolor` ラベルの色; デフォルト値 = `color`

`backgroundcolor` ラベルの背景色; labelrsep が 0 の場合、背景色 "white" を使用できます; デフォルト値 = "none"

`arrowstyle1` 弧の開始の矢印スタイル; デフォルト値 = "."; 有効な文字列は:

  * `.` ドットマーカー
  * `<|-` 矢印

`arrowstyle2` 弧の終了の矢印スタイル; デフォルト値 = "-|>"; 有効な文字列は:

  * `.` ドットマーカー
  * `-|>` 矢印

`headlength` 矢印の頭の長さ; デフォルト値 = 5

`headwidth` 矢印の頭の幅; デフォルト値 = 2.5

# 例

コードをコピーして貼り付けます:

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
