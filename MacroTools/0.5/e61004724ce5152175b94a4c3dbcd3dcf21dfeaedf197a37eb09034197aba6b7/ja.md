```
splitdef(fdef)
```

任意の関数定義に一致します

```julia
function name{params}(args; kwargs)::rtype where {whereparams}
   body
end
```

そして `Dict(:name=>..., :args=>..., etc.)` を返します。定義は `MacroTools.combinedef(dict)` を呼び出すことで再構築できます。

参照: [`combinedef`](@ref)
