```
SaintVenantKirchhoff
```

Saint-Venant-Kirchhoff 構成モデルは、[`CMaterial`](@ref) および [`BACMaterial`](@ref) を使用する際に指定できます。最初のピオラ-キルヒホッフ応力 $\boldsymbol{P}$ は次のように与えられます。

$$
\begin{aligned}
\boldsymbol{E} &= \frac{1}{2} \left( \boldsymbol{F}^{\top} \boldsymbol{F} - \boldsymbol{I}
                              \right) \; , \\
\boldsymbol{S} &= \lambda \, \mathrm{tr}(\boldsymbol{E}) \, \boldsymbol{I}
                + 2 \mu \boldsymbol{E} \; , \\
\boldsymbol{P} &= \boldsymbol{F} \, \boldsymbol{S} \; ,
\end{aligned}
$$

変形勾配 $\boldsymbol{F}$、グリーン-ラグランジュひずみテンソル $\boldsymbol{E}$、第二ピオラ-キルヒホッフ応力 $\boldsymbol{S}$、および第一および第二ラメパラメータ $\lambda$ と $\mu$ で構成されています。
