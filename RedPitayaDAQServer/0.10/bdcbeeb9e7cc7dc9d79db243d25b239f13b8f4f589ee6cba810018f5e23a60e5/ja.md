```
offsetDAC(rp::RedPitaya, channel)
```

`channel`のオフセットを返します。

[`offsetDAC!`](@ref)を参照してください。

# 例

```julia
julia> offsetDAC!(rp, 1, 0.2);
true

julia> offsetDAC(rp, 1)
0.2
```
