```
twist(tsrc::AbstractTensorMap, i::Int; inv::Bool=false) -> tdst
twist(tsrc::AbstractTensorMap, is; inv::Bool=false) -> tdst
```

`tsrc`の`i`番目のインデックスにツイストを適用し、結果を新しいテンソルとして返します。`inv=true`の場合は、逆ツイストを使用します。

結果をその場で保存するには、[`twist!`](@ref)を参照してください。
