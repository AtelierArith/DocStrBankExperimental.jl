```
setting(xf::TransformVariables.AbstractTransform) :: Lens
```

Lens to set value transformed by `xf` (and get value via the inverse transformation).

# Examples

```jldoctest
julia> using Setfield, Kaleido, TransformVariables

julia> l = (@lens _.y[2]) ∘ setting(as𝕀)
(@lens _.y[2]) ∘ (←|as𝕀→)

julia> obj = (x=0, y=(1, 0.5, 3));

julia> get(obj, l)
0.0

julia> @assert set(obj, l, Inf).y[2] ≈ 1

julia> @assert set(obj, l, -Inf).y[2] ≈ 0.0
```
