```
NeoHooke
```

ネオフックの構成モデルは、[`CMaterial`](@ref)および[`BACMaterial`](@ref)を使用する際に指定できます。最初のピオラ-キルヒホッフ応力 $\boldsymbol{P}$ は次のように与えられます。

$$
\begin{aligned}
\boldsymbol{C} &= \boldsymbol{F}^{\top} \boldsymbol{F} \; , \\
\boldsymbol{S} &= \mu \left( \boldsymbol{I} - \boldsymbol{C}^{-1} \right)
    + \lambda \log(J) \boldsymbol{C}^{-1} \; , \\
\boldsymbol{P} &= \boldsymbol{F} \, \boldsymbol{S} \; ,
\end{aligned}
$$

変形勾配 $\boldsymbol{F}$、右コーシー-グリーン変形テンソル $\boldsymbol{C}$、ヤコビアン $J = \mathrm{det}(\boldsymbol{F})$、第二ピオラ-キルヒホッフ応力 $\boldsymbol{S}$、および第一および第二ラメパラメータ $\lambda$ と $\mu$。
