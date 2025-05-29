```
frequencyDAC(rp::RedPitaya, channel, component)
```

`channel`の合成波形`component`の周波数を返します。

[`frequencyDAC!`](@ref)を参照してください。

# 例

```julia
julia> frequencyDAC!(rp, 1, 1, 2400);
true

julia> frequencyDAC(rp, 1, 1)
2400
```
