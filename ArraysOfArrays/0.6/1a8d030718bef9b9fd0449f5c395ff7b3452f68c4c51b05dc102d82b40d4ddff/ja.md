```
innermap(f::Base.Callable, A::AbstractArray{<:AbstractArray})
```

深さ2のネストされた`map`。`map(X -> map(f, X), A)`に相当します。
