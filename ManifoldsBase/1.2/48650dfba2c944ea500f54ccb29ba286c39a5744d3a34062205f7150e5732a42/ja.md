```
PadeRetraction{m} <: AbstractRetractionMethod
```

$ m $ 次のパデ近似に基づく再収束

# コンストラクタ

```
PadeRetraction(m::Int)
```

!!! note "技術的注意"
    例えば [`retract`](@ref)`(M, p, X, PadeRetraction(m))` と呼び出してパデ再収束を実装しますが、あなたの多様体 `M` のために [`retract_pade!`](@ref)`(M, q, p, X, t, m)` を定義してください。

