```julia
ComplexNormal(μ,σ)
```

  * `μ` : 平均、デフォルトは `μ = 0`
  * `σ` : 標準偏差、デフォルトは `σ  =1`

```julia
# 例

# 10個の独立同分布の標準複素ガウス乱数変数を生成
rand(ComplexNormal(), 10) 

# 平均 1+1im、分散 4 の複素正規分布を生成
rand(ComplexNormal(1+1im,2)) 
```
