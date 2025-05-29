```
register(source, target; upsample_factor=1)
```

`target`画像を`source`画像に登録するには、まず位相オフセット（[`phase_offset`](@ref)）を見つけ、その後[`fourier_shift`](@ref)を使って`target`をフーリエシフトします。

# 例

```jldoctest
julia> image = reshape(1.0:100.0, 10, 10);

julia> shift = (-1.6, 2.8)
(-1.6, 2.8)

julia> target = fourier_shift(image, shift);

julia> target_shift = register(image, target; upsample_factor=5);
```

# 参照

[`phase_offset`](@ref)
