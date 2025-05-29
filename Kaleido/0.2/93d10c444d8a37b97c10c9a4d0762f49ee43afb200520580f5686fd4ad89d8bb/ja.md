```
settingas𝕀 :: BijectionLens
```

これは、TransformVariables.jlなしで動作する`setting(as𝕀)`の簡略版です。

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> l = (@lens _.y[2]) ∘ settingas𝕀
(@lens _.y[2]) ∘ (←logistic|logit→)

julia> obj = (x=0, y=(0, 0.5, 2));

julia> get(obj, l)
0.0

julia> @assert set(obj, l, Inf).y[2] ≈ 1

julia> @assert set(obj, l, -Inf).y[2] ≈ 0
```
