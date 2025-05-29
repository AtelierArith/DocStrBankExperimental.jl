```
const CONJUNCTION = NamedConnective{:∧}()
const ∧ = CONJUNCTION
arity(::typeof(∧)) = 2
```

論理的な連言。`\wedge<tab>`で入力できます。

関連情報としては、[`NamedConnective`](@ref)、[`Connective`](@ref)があります。
