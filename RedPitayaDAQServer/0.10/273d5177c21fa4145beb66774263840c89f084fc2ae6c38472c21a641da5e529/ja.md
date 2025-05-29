```
phaseDAC!(rp::RedPitaya, channel, component, value)
```

合成波形 `component` の位相を `channel` に設定します。コマンドが成功した場合は `true` を返します。

[`phaseDAC`](@ref) を参照してください。

# 例

```julia
julia> phaseDAC!(rp, 1, 1, 0.0);
true

julia> phaseDAC(rp, 1, 0.0)
0.0
```
