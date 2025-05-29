```
phaseDAC(rp::RedPitaya, channel, component)
```

チャネルのコンポーネント`component`の合成波形の位相を返します。

[`phaseDAC!`](@ref)を参照してください。

# 例

```julia
julia> phaseDAC!(rp, 1, 1, 0.0);
true

julia> phaseDAC(rp, 1, 0.0)
0.0
```
