```
ismodal(::Type{<:Connective})::Bool = false
ismodal(c::Connective)::Bool = ismodal(typeof(c))
```

`Connective` がモーダルであることが知られているかどうかを返します。

# 例

```julia-repl
julia> ismodal(◊)
true

julia> ismodal(∧)
false
```
