# 関数呼び出し

```
phasorcosine_hline(phasorcosine_hline(mag = 1, phi = 0; color="black",
linewidth = 1, linestyle = ":", colorDash="gray", shift = true, marker="")
```

# 説明

この関数は `phasorcosine` を使用した後に適用できます。左のサブプロットのファゾールと右のサブプロットのコサイン波の間に水平線を描画します。

# 変数

`mag` 表示されるファゾールの大きさ; 0 と 1 の間でなければならない; デフォルト値 = 1

`phi` ファゾールの位相角; デフォルト値 = 0

`color` ファゾールの色; すなわち、シャフトと矢印の色; デフォルト値 = "black"

`linewidth` 水平線の線幅; デフォルト値 = 1

`linestyle` 水平線の線スタイル; デフォルト値 = ":"

`colorDash` 点線の円（左のサブプロット）と左と右のサブプロット間の水平点線の色; デフォルト値 = "gray"

`gapcolor` 線の隙間の色; デフォルト値 = 何も指定しない

`shift` `true` の場合、右のコサイン曲線は位相シフト `phi` でプロットされる; デフォルト値 = `true`

`marker` `""` でない場合、右のプロットにマーカーが使用される; デフォルト値 = `""`

# 例

コードをコピーして貼り付けます:

```julia
using Unitful, Unitful.DefaultSymbols, PyPlot, ElectricalEngineering
phasorcosine(1, 0°, ylabel=L"$i$", maglabel=L"$\hat{I}$",
labelrelrot = false, color="black", linewidth=1.5, xlabel=L"\beta/{^\circ}",
shift = false, marker = "o")
subplot(121)
phasor(j * pol(1,30°),color=colorBlack2,linestyle=lineStyle2)
phasorcosine_hline(1, 30°, color=colorBlack2, shift=false, marker="o")
```
