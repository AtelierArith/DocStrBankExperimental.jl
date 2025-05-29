```
signalTypeDAC!(rp::RedPitaya, channel, value)
```

`channel`の合成波形のsignalTypeを返します。

[`signalTypeDAC!`](@ref)を参照してください。

# 例

```julia
julia> signalTypeDAC!(rp, 1, SINE);
true

julia> signalTypeDAC(rp, 1)
SINE
```
