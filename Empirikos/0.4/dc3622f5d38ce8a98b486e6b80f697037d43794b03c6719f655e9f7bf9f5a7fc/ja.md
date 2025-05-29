```
StatsBase.confint(method::AMARI,
                  target::Empirikos.EBayesTarget,
                  Zs;
                  level=0.95)
```

[`Empirikos.EBayesTarget`](@ref) `target` の信頼区間を、サンプル `Zs` に基づいて、`AMARI`(@ref) `method` を使用して、カバレッジ `level` で形成します。
