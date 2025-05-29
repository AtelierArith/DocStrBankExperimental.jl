```
num_occupied_modes(::SingleComponentFockAddress)
```

アドレス内の占有モードの数を取得します。`length(`[`occupied_modes`](@ref)`(address))`と同等で、ONR表現における非ゼロの数です。

# 例

```jldoctest
julia> num_occupied_modes(BoseFS((1, 0, 2)))
2
julia> num_occupied_modes(FermiFS((1, 1, 1, 0)))
3
```

[`SingleComponentFockAddress`](@ref)を参照してください。
