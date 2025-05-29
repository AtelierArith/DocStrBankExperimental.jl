```
amplitudeDAC!(rp::RedPitaya, channel, component, value)
```

合成波形 `component` の振幅を `channel` に設定します。コマンドが成功した場合は `true` を返します。

[`amplitudeDAC`](@ref) を参照してください。

# 例

```julia
julia> amplitudeDAC!(rp, 1, 1, 0.5);
true

julia> amplitudeDAC(rp, 1, 1)
0.5
```
