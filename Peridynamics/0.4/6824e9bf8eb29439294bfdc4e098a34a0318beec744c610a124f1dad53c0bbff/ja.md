```
MooneyRivlin
```

Mooney-Rivlin 構成モデルは、[`CMaterial`](@ref) および [`BACMaterial`](@ref) を使用する際に指定できます。最初のピオラ-キルヒホッフ応力 $\boldsymbol{P}$ は次のように与えられます。

$$
\begin{aligned}
\boldsymbol{C} &= \boldsymbol{F}^{\top} \boldsymbol{F} \; , \\
\boldsymbol{S} &= G \left( \boldsymbol{I} - \frac{1}{3} \mathrm{tr}(\boldsymbol{C})
                           \boldsymbol{C}^{-1} \right) \cdot J^{-\frac{2}{3}}
                + \frac{K}{4} \left( J^2 - J^{-2} \right) \boldsymbol{C}^{-1} \; , \\
\boldsymbol{P} &= \boldsymbol{F} \, \boldsymbol{S} \; ,
\end{aligned}
$$

変形勾配 $\boldsymbol{F}$、右コーシー-グリーン変形テンソル $\boldsymbol{C}$、ヤコビアン $J = \mathrm{det}(\boldsymbol{F})$、第二ピオラ-キルヒホッフ応力 $\boldsymbol{S}$、せん断弾性率 $G$、および体積弾性率 $K$ で構成されています。

# エラーハンドリング

ヤコビアン $J$ が機械精度 `eps()` より小さいか `NaN` の場合、最初のピオラ-キルヒホッフ応力テンソルは $\boldsymbol{P} = \boldsymbol{0}$ と定義されます。
