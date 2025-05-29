```
MaximumAPosterioriBayesian(prior, optimmethod, x0; islog, lowerbounds, upperbounds)
```

[`bayesianupdating`](@ref) に渡され、`x0` から始めて事後分布の1つ以上の最大値を推定します。最適化は `optimmethod` で指定された方法を使用します。`x0` の各点ごとに1つの推定を計算します。フラグ `islog` は、[`bayesianupdating`](@ref) メソッドに渡される事前および尤度関数がすでに対数として与えられているかどうかを指定します。`lowerbounds` と `upperbounds` は最適化の区間を指定します。

代替コンストラクタ

```julia
    MaximumAPosterioriBayesian(prior, optimmethod, x0; islog) # `lowerbounds` = [-Inf], # `upperbounds` = [Inf]
    MaximumAPosterioriBayesian(prior, optimmethod, x0)  # `islog` = true
```

[`MaximumLikelihoodBayesian`](@ref)、[`bayesianupdating`](@ref)、[`TransitionalMarkovChainMonteCarlo`](@ref) も参照してください。
