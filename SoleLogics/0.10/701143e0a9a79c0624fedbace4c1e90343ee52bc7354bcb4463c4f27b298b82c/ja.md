```
const IMPLICATION = NamedConnective{:→}()
const → = IMPLICATION
arity(::typeof(→)) = 2
```

論理的含意。 `\to<tab>` と入力できます。

関連項目 [`NamedConnective`](@ref), [`Connective`](@ref).
