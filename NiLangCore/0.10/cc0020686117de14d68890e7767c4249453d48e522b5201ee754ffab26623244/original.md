```
@i function fname(args..., kwargs...) ... end
@i struct sname ... end
```

Define a reversible function/type.

```jldoctest; setup=:(using NiLangCore)
julia> @i function test(out!, x)
           out! += identity(x)
       end

julia> test(0.2, 0.8)
(1.0, 0.8)
```

See `test/compiler.jl` for more examples.
