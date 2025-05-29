```
lens₁ ∘ lens₂
```

Compose lenses `lens₁`, `lens₂`, ..., `lensₙ` to access nested objects.

# Example

```jldoctest
julia> using Setfield

julia> obj = (a = (b = (c = 1,),),);

julia> la = @lens _.a
       lb = @lens _.b
       lc = @lens _.c
       lens = la ∘ lb ∘ lc
(@lens _.a.b.c)

julia> get(obj, lens)
1
```
