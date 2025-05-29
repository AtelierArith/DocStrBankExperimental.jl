```
const DISJUNCTION = NamedConnective{:∨}()
const ∨ = DISJUNCTION
arity(::typeof(∨)) = 2
```

論理和。`\vee<tab>`で入力できます。

関連項目としては、[`NamedConnective`](@ref)、[`Connective`](@ref)があります。
