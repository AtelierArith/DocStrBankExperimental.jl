```
const NEGATION = NamedConnective{:¬}()
const ¬ = NEGATION
arity(::typeof(¬)) = 1
```

論理否定（補集合とも呼ばれます）。`\neg<tab>`で入力できます。

関連情報としては、[`NamedConnective`](@ref)、[`Connective`](@ref)があります。
