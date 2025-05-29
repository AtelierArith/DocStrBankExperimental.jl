```
splitdef(fdef)
```

Match any function definition

```julia
function name{params}(args; kwargs)::rtype where {whereparams}
   body
end
```

and return `Dict(:name=>..., :args=>..., etc.)`. The definition can be rebuilt by calling `MacroTools.combinedef(dict)`.

See also: [`combinedef`](@ref)
