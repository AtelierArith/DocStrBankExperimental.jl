```
chfield(x, field, val)
```

オブジェクト `x` の `field` を変更します。

`field` は `Val` 型であることができます。

```jldoctest; setup=:(using NiLangCore)
julia> chfield(1+2im, Val(:im), 5)
1 + 5im
```

または関数であることもできます。

```jldoctest; setup=:(using NiLangCore)
julia> using NiLangCore

julia> struct GVar{T, GT}
           x::T
           g::GT
       end

julia> @fieldview xx(x::GVar) = x.x

julia> chfield(GVar(1.0, 0.0), xx, 2.0)
GVar{Float64, Float64}(2.0, 0.0)
```
