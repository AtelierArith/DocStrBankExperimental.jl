```
prox!(regType::Type{<:AbstractProjectionRegularization}, x; kwargs...)
```

与えられた `kwargs` で `regType` 型の正則化項を構築し、その `prox!` を `x` に適用します。
