# 関数呼び出し

```
phasorcosine(mag = 1, phi = 0; add = false, figsize = (6.6,2.5),
    xlabel = L"$\omega\!\cdot\!t/^\circ $", ylabel = "", maglabel = "",
    phasorlabel = maglabel, labeltsep = 0.1, labelrsep = 0.5,
    labelrelrot = true, labelrelangle = 0,
    color = "black", linewidth = 1, linestyle = "-",
    colorDash="gray", left=0.20, right=0.80, bottom=0.20, top=0.80,
    showcosine=true, showdashline=true)
```

# 説明

この関数は、図の左のサブプロットに0から1の間の大きさを持つファゾールを描画し、右のサブプロットにコサイン図を描画します。このようなグラフは、電気工学においてファゾールと時間領域の波形との関係を説明するために使用されます。

# 変数

`mag` 表示されるファゾールの大きさ; 0から1の間でなければならない; デフォルト値 = 1

`phi` ファゾールの位相角; デフォルト値 = 0

`add` この関数を初めて呼び出すとき、`add` は `false` に等しくなければならず、これはデフォルト値です。この場合、`figsize` で指定された寸法の新しい図が作成されます。既存の図に2つ目のファゾールとコサイン図を追加するには、`add` を `true` に設定する必要があります。

`figsize` 新しい図のサイズ、`add` が `false` の場合; デフォルト値 = (7,2.5)

`xlabel` 右のサブプロットのx軸のラベル; デフォルト値 ="ωt/°"（LaTeX表記）

`ylabel` 右のサブプロットのy軸のラベル; デフォルト値 = ""; 1つ以上のファゾールとコサイン図を描画する場合（`add = true`）、このラベルは1回だけ表示されます。したがって、関数 `phasorcosine` が最初に呼び出されるときにすべてのファゾールのラベルを作成する必要があります。

`maglabel` 右のサブプロットの正および負の大きさ `mag` のラベル; デフォルト値 = "";

`phasorlabel` 左のサブプロットのファゾールのラベル; デフォルト値 = `maglabel`

`labelrsep` ラベルの放射方向の位置（ファゾールの方向に沿って）: `labelrsep = 0` はファゾールのシャフトを表し、`labelrsep = 1` はファゾールの矢印の先端を表します; デフォルト値 = 0.5、すなわちファゾールの放射中心

`labeltsep` ラベルの接線方向の位置: `labeltsep = 0` はラベルがファゾールにプロットされることを意味します; `labeltsep = 0.1` はラベルをファゾールの上にプロットし、`ref` に対して10%の変位を適用します; `labeltsep = -0.2` はラベルをファゾールの下にプロットし、`ref` に対して20%の変位を適用します; デフォルト値 = 0.1

`labelrelrot` ラベルの相対回転; `labelrelrot == false`（デフォルト値）の場合、ラベルはファゾールの方向に対して回転しません; それ以外の場合、ラベルは `labelrelangle` の角度でファゾールに対して回転します。

`labelrelangle` ファゾールの方向に対するラベルの相対角度; この角度は、`labelrelrot == true` の場合にのみ適用されます; この角度は、ファゾールの方向に対するラベルの相対的な方向を示します; デフォルト値 = 0

`color` ファゾールの色; すなわち、シャフトと矢印の先端の色; デフォルト値 = "black"

`backgroundcolor` すべてのラベルの背景色; labelrsep が0の場合、背景色 "white" を使用できます; デフォルト値 = "none"

`linewidth` ファゾールの線の幅; デフォルト値 = 1

`linestyle` ファゾールの線のスタイル; デフォルト値 = "-"

`colorDash` （左のサブプロットの）破線の円と左と右のサブプロットの間の水平破線の色; デフォルト値 = "gray"

`left` 図の左側; デフォルト値 = 0.2

`right` 図の右側; デフォルト値 = 0.85

`bottom` 図の下側; デフォルト値 = 0.2

`top` 図の上側; デフォルト値 = 0.85

`showcosine` `true` の場合、コサイン波が表示されます; デフォルト値 = `true`

`showdashline` `true` の場合、破線が表示されます; デフォルト値 = `true`

`shift` `true` の場合、右のコサイン曲線は位相シフト `phi` でプロットされます; デフォルト値 = `true`

`marker` `""` でない場合、右のプロットにマーカーが使用されます; デフォルト値 = `""`

# 例

コードをコピーして貼り付けます:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
rc("text", usetex=true); rc("font", family="serif")
phasorcosine(1, 45°, ylabel=L"$u,i$", maglabel=L"$\hat{U}$", labelrsep=0.3,
    color="gray", linestyle="--")
phasorcosine(0.55, 0, add=true, maglabel=L"$\hat{I}$")
# save2fig("phasorcosine",crop=true)
```
