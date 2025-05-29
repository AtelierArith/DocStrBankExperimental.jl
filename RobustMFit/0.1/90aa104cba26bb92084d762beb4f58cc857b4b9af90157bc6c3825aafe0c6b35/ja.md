```
Mfit(x::Vector{Real}, d::UnivariateDistribution, spec::MSetting;
     type::Union{Symbol, String} = :ψ, MM::Bool = true, biasCorr = :L)
Mfit(x::Vector{Real}, d::UnivariateDistribution, spec::Vector{MSetting};
     type::Union{Symbol, String} = :ψ, MM::Bool = true, biasCorr = :L)
```

M推定を使用して、サンプル`x`に対して単変量分布`d`をフィッティングします。`d`に推定する複数のパラメータがある場合、異なる仕様を提供できます。1つの仕様のみが追加された場合、それはすべての推定方程式に使用されます。

`type`は、損失関数、その導関数、または重み関数に基づく推定のタイプ(:ρ, :ψまたは:w)を指定します。

`MM`を`true`に設定すると、生のモーメントの推定が行われ、その後、推定値がパラメータに変換されます。`MM = false`の場合、パラメータは直接推定されます。この場合、ψタイプの推定のみが実行できます。

`biasCorr`はバイアス補正のタイプを指定します。`:L`は下限調整定数の更新を示し、`:U`は上限調整定数の更新を示し、`biasCorr = :C`は補正項に基づく推定を行い、`:N`はバイアス補正を含めません。

デフォルトは、下限調整定数を更新するモーメントに基づくψタイプの推定です。

# 例

```julia
d = Poisson(10)
x = rand(d, 200)
spec = Huber(1.5)
Mfit(x, d, spec)

d = Normal()
x = rand(d, 200)
spec = [Huber(1.5), Huber(2.5)]
Mfit(x, d, spec)
```
