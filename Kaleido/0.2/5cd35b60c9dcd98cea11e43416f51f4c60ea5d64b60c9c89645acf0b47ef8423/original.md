```
ToField(f) :: Setter
```

Apply `f` when setting.  Use `x -> get(x, f)` if `f` is a `Lens`.

# Examples

```jldoctest
julia> using Setfield, Kaleido

julia> setter = (@lens _.x) ∘ ToField(@lens _.a)
(@lens _.x) ∘ (←(@lens _.a)|❌→)

julia> set((x = 1, y = 2), setter, (a = 10, b = 20))
(x = 10, y = 2)
```
