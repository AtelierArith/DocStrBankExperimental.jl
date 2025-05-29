```
@i function fname(args..., kwargs...) ... end
@i struct sname ... end
```

可逆関数/型を定義します。

```jldoctest; setup=:(using NiLangCore)
julia> @i function test(out!, x)
           out! += identity(x)
       end

julia> test(0.2, 0.8)
(1.0, 0.8)
```

詳細な例については `test/compiler.jl` を参照してください。
