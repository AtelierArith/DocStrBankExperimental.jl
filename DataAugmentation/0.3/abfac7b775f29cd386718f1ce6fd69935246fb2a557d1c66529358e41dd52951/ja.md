```
Reflect(γ)
Reflect(distribution)
```

中心を中心に、[-γ, γ]の範囲から一様に選ばれた角度で2D空間データを反射します。角度は度単位で指定されます。

角度を選択するために、任意の`Distributions.Sampleable`を渡すこともできます。

## 例

```julia
tfm = Reflect(10)
```
