```
Signatures <: EnergyMap
```

署名に基づくエネルギーマップで、地球移動者距離（EMD）を使用して座標の識別測定を計算する測定値です。署名は、EMDと効率的に使用できる完全にデータ駆動型の表現を提供します。この表現はヒストグラムよりも効率的で、より少ないサンプルで複雑なデータ構造を表現することができます。

ここでは、クラス$c$の$j$-thレベル、$k$-thノード、$l$-thインデックスの係数に対する署名を次のように定義します。

$$
s_{j,k,l}^{(c)} = \{(\alpha_{i;j,k,l}^{(c)}, w_{i;j,k,l}^{(c)})\}_{i=1}^{N_c}
$$

ここで、$\alpha_{i;j,k,l}^{(c)}$と$w_{i;j,k,l}^{(c)}$は、それぞれクラス$c$の信号$i$の位置$(j,k,l)$での展開係数と重みです。現在、2つの有効な重みのタイプは`：equal`と`：pdf`です。

# パラメータ

  * `weight::Symbol`: (デフォルト: `:equal`) $w_{i;j,k,l}^{(c)}$を計算するために使用される重みのタイプ。利用可能なメソッドは`：equal`と`：pdf`です。

**参照:** [`EnergyMap`](@ref), [`TimeFrequency`](@ref), [`ProbabilityDensity`](@ref)
