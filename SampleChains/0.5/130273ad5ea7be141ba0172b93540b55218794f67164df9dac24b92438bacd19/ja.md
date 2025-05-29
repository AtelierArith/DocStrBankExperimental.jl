```
logq(chain::AbstractChain) -> AbstractVector{AbstractFloat}
```

サンプリングされたチェーンの対数密度のベクトルを返します。次の条件を満たす必要があります。

```
logq(chain) == getlogdensity(chain).(samples(chain))
```
