```
ContextError <: Exception
ContextError(::Type, ::Type, ::Symbol)
```

不正な型の値を返したことを示す`Exception`です。これは[`context`](@ref)キーによって返されました。

# 例

```jldoctest
julia> ContextError(Mode, String, :mode)
ContextError(Mode, String, :mode)
```
