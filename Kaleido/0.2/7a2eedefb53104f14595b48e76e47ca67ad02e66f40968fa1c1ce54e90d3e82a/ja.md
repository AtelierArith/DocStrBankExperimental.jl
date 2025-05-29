```
converting(; fromfield, tofield) :: Lens
```

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> halve(x) = x / 2;

julia> double(x) = 2x;

julia> l = (@lens _.y[2]) ∘ converting(fromfield = halve, tofield = double)
(@lens _.y[2]) ∘ (←double|halve→)

julia> obj = (x=0, y=(1, 2, 3));

julia> @assert get(obj, l) == 1.0 == 2/2

julia> set(obj, l, 0.5)
(x = 0, y = (1, 1.0, 3))
```
