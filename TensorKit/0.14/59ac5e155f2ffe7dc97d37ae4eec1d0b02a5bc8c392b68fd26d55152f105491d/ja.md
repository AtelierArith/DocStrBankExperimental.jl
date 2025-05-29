```
twist!(t::AbstractTensorMap, i::Int; inv::Bool=false) -> t
twist!(t::AbstractTensorMap, is; inv::Bool=false) -> t
```

`t`の`i`番目のインデックス、または`is`のすべてのインデックスにツイストを適用し、結果を`t`に格納します。`inv=true`の場合は、逆ツイストを使用します。

新しいテンソルを作成するには、[`twist`](@ref)を参照してください。
