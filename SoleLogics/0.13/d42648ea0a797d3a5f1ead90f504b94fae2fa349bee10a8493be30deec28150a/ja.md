```
struct BooleanTruth <: Truth
    flag::Bool
end
```

ブール真理値 ⊤ と ⊥ を表す構造体です。フラグをラップしており、⊤ の場合は `true` ([`TOP`](@ref))、⊥ の場合は `false` ([`BOT`](@ref)) となります。

関連情報として [`BooleanAlgebra`](@ref) も参照してください。
