```
amplitudeDAC(rp::RedPitaya, channel, component)
```

チャネルの合成波形 `component` の振幅を返します。

[`amplitudeDAC!`](@ref) を参照してください。

# 例

```julia
julia> amplitudeDAC!(rp, 1, 1, 0.5);
true

julia> amplitudeDAC(rp, 1, 1)
0.5
```
