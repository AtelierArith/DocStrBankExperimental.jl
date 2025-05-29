```
prox!(regType::Type{<:AbstractParameterizedRegularization}, x, λ; kwargs...)
```

与えられた `λ` と `kwargs` で `regType` 型の正則化項を構築し、`x` にその `prox!` を適用します。
