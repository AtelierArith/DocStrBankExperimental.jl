```
const CONJUNCTION = NamedConnective{:∧}()
const ∧ = CONJUNCTION
arity(::typeof(∧)) = 2
```

論理的な連言。`\wedge<tab>`で入力できます。

関連項目 [`NamedConnective`](@ref), [`Connective`](@ref).
