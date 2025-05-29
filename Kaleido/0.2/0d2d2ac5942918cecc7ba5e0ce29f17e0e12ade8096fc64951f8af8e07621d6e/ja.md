```
settingasℝ₊ :: BijectionLens
```

これは、TransformVariables.jlなしで動作する`setting(asℝ₊)`の簡略版です。

# 例

```jldoctest
julia> using Setfield, Kaleido

julia> l = (@lens _.y[2]) ∘ settingasℝ₊
(@lens _.y[2]) ∘ (←exp|log→)

julia> obj = (x=0, y=(0, 1, 2));

julia> @assert get(obj, l) == 0.0 == log(obj.y[2])

julia> @assert set(obj, l, -1) == (x=0, y=(0, exp(-1), 2))
```
