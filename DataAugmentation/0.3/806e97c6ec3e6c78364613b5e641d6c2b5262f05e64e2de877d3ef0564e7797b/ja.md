```
Rotate(γ)
Rotate(distribution)
Rotate(α, β, γ)
Rotate(α_distribution, β_distribution, γ_distribution)
```

中心を中心に空間データを回転させます。Rotate(γ)は、[-γ, γ]の範囲から一様に選ばれた角度による2D回転で、角度は度数法で指定されます。Rotate(α, β, γ)は、X、Y、Z回転のために[-α, α]、[-β, β]、[-γ, γ]の範囲から一様に選ばれた角度による3D回転です。

角度が選択される任意の`Distributions.Sampleable`を渡すこともできます。

## 例

```julia
tfm2d = Rotate(10)
apply(tfm2d, Image(rand(Float32, 16, 16)))

tfm3d = Rotate(10, 20, 30)
apply(tfm3d, Image(rand(Float32, 16, 16, 16)))
```
