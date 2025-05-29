```
signalTypeDAC!(rp::RedPitaya, channel, value)
```

`channel`の合成波形のsignalTypeを設定します。コマンドが成功した場合は`true`を返します。

[`signalTypeDAC`](@ref)を参照してください。

# 例

```julia
julia> signalTypeDAC!(rp, 1, SINE);
true

julia> signalTypeDAC(rp, 1)
SINE
```
