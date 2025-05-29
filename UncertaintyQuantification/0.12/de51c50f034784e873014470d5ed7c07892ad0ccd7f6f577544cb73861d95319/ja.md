```
TransitionalMarkovChainMonteCarlo(prior, n, burnin, β, islog)

[`bayesianupdating`](@ref) に渡され、[`RandomVariable'](@ref) ベクトル `prior` を使用して遷移マルコフ連鎖モンテカルロアルゴリズムを実行します。各遷移レベルで、`burnin` ステップが破棄された後、`n` 個の独立したマルコフ連鎖から1つのサンプルが生成されます。フラグ `islog` は、[`bayesianupdating`](@ref) メソッドに渡される事前分布と尤度関数がすでに対数として与えられているかどうかを指定します。
```

Alternative constructors

```julia
    TransitionalMarkovChainMonteCarlo(prior, n, burnin, β)  # `islog` = true
     TransitionalMarkovChainMonteCarlo(prior, n, burnin)    # `β` = 0.2,  `islog` = true
```

# References

[chingTransitionalMarkovChain2007](@cite)
