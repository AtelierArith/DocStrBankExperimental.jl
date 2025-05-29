```
add_resolution_column!(particle_data::AbstractDataFrame)
```

`original_video`に対応するデータのビデオフレームを見て、型がTuple{Int, Int}の解像度の列を追加します。関数名の`!`によって示されるように、`particle_data`をその場で修正します。

[`getvideoresolution`](@ref)を使用します。
