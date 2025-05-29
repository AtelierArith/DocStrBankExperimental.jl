```
sysr, hs = frequency_weighted_reduction(G, Wo, Wi, r=nothing; residual=true)
```

$$
||Wₒ(G-Gr)Wᵢ||∞
$$

を最小化する Gr を見つけます。相対的な削減を行う場合は、Wo = inv(G) および Wi = I に設定します。

`residual = true` の場合、マッチした静的ゲインは「残差化」によって達成されます。すなわち、

$$
0 = A_{21}x_{1} + A_{22}x_{2} + B_{2}u
$$

ここで、インデックス 1/2 はそれぞれ残りの状態/切り捨てられた状態に対応します。この選択は通常、低周波領域でのマッチが向上し、全体的な誤差が小さくなる結果をもたらします。

参考文献: [Andras Varga and Brian D.O. Anderson, "Accuracy enhancing methods for the frequency-weighted balancing related model reduction"](https://elib.dlr.de/11746/1/varga_cdc01p2.pdf)

注意: この関数は指数安定モデルのみを扱います。不安定および限界安定モデルを削減するには、[`stab_unstab`](@ref) を使用してシステムを安定部分と不安定部分に分解し、安定部分を削減した後、不安定部分を再度追加します。

# 例:

以下の例は、周波数 `w1` と `w2` の間に焦点を当てた削減を行います。

```julia
using DSP
w1 = 1e-4
w2 = 1e-1
fc = DSP.analogfilter(DSP.Bandpass(w1, w2), DSP.Butterworth(2))
tfc = DSP.PolynomialRatio(fc)
W = tf(DSP.coefb(tfc), DSP.coefa(tfc))
rsys, hs = frequency_weighted_reduction(sys, W, 1)
```
