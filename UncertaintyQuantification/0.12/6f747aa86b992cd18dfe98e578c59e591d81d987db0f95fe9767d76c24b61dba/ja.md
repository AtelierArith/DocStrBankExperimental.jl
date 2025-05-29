```
MaximumLikelihoodBayesian(prior, optimmethod, x0; islog, lowerbounds, upperbounds)
```

[`bayesianupdating`](@ref) に渡され、`x0` から始めて尤度の1つ以上の最大値を推定します。最適化は `optimmethod` で指定された方法を使用します。`x0` の各点ごとに1つの推定を計算します。フラグ `islog` は、[`bayesianupdating`](@ref) メソッドに渡される事前分布と尤度関数がすでに対数として与えられているかどうかを指定します。`lowerbounds` と `upperbounds` は最適化の区間を指定します。

代替コンストラクタ

```julia
    MaximumLikelihoodBayesian(prior, optimmethod, x0; islog) # `lowerbounds` = [-Inf], # `upperbounds` = [Inf]
    MaximumLikelihoodBayesian(prior, optimmethod, x0)  # `islog` = true
```

### 注意事項

このメソッドは、最適化されるべきパラメータに関する情報としてのみ `prior` を使用します。事前分布自体は最大尤度推定の結果に影響を与えず、ダミー分布として与えることができます。たとえば、2つのパラメータ `a` と `b` が最適化されるべき場合、事前分布は次のようになります。

```julia
    prior = RandomVariable.(Uniform(0,1), [:a, :b])
```

[`MaximumAPosterioriBayesian`](@ref)、[`bayesianupdating`](@ref)、[`TransitionalMarkovChainMonteCarlo`](@ref) も参照してください。
