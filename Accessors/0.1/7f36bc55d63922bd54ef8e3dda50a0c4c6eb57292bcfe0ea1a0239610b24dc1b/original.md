```
optic₁ ⨟ optic₂
```

Compose optics `optic₁`, `optic₂`, ..., `opticₙ` to access nested objects.

# Example

```jldoctest
julia> using Accessors

julia> obj = (a = (b = (c = 1,),),);

julia> la = @optic _.a
       lb = @optic _.b
       lc = @optic _.c
       lens = la ⨟ lb ⨟ lc
(@o _.c) ∘ ((@o _.a.b))

julia> lens(obj)
1
```
