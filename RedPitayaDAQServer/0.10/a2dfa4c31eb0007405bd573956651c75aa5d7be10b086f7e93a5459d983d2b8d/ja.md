```
offsetDAC!(rp::RedPitaya, channel, value)
```

`channel`のオフセットを設定します。コマンドが成功した場合は`true`を返します。

[`offsetDAC`](@ref)を参照してください。

# 例

```julia
julia> offsetDAC!(rp, 1, 0.2);
true

julia> offsetDAC(rp, 1)
0.2
```
