```
LinearElastic
```

線形弾性材料モデルは、[`CMaterial`](@ref)および[`BACMaterial`](@ref)を使用する際に指定できます。最初のピオラ-キルヒホッフ応力 $\boldsymbol{P}$ は次のように与えられます。

$$
\boldsymbol{P} = \mathbb{C} : \boldsymbol{E} \; ,
$$

弾性剛性テンソル $\mathbb{C}$ とグリーン-ラグランジュひずみテンソル $\boldsymbol{E}$ は次のように定義されます。

$$
\boldsymbol{E} = \frac{1}{2} \left( \boldsymbol{F}^{\top} \boldsymbol{F} - \boldsymbol{I}
                             \right) \; .
$$
