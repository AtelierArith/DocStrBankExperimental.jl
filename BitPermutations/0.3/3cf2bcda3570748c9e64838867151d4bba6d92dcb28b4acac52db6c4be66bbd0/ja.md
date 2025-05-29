```
invbitpermute(x::Number, p::AbstractBitPermutation)
invbitpermute(x::Number, backend::PermutationBackend)
invbitpermute(x::AbstractArray{T}, P::AbstractBitPermutation{T})
```

`x`のビットの逆順置換を`AbstractBitPermutation`を使用して実行します。`p`で指定された置換の逆を使用します。構文`p'(x)`も使用できます。内部的に、置換操作は`PermutationBackend`として保存されるため、バックエンドを直接使用して置換を呼び出すことができます。入力が`AbstractArray`のサブタイプである場合、逆順置換は要素ごとに実行されます。これも`p'.(x)`または`invbitpermute.(x, p)`で呼び出すことができます。入力配列がその後必要ない場合は、インプレースバージョン`invbitpermute!`が推奨されます。

[`bitpermute`](@ref)や[`invbitpermute!`](@ref)も参照してください。
