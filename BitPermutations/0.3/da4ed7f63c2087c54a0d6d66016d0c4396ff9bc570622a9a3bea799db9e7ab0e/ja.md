```
bitpermute(x::Number, p::AbstractBitPermutation)
bitpermute(x::Number, backend::PermutationBackend)
bitpermute(x::AbstractArray{T}, p::AbstractBitPermutation{T})
```

`x`のビットを`AbstractBitPermutation`を使用して置換を行い、`p`で指定された置換を使用します。`p(x)`という構文も使用できます。内部的には、置換操作は`PermutationBackend`として保存されるため、バックエンドを直接使用して置換を呼び出すことができます。入力が`AbstractArray`のサブタイプである場合、置換は要素ごとに実行されます。これも`p.(x)`または`bitpermute.(x, p)`で呼び出すことができます。入力配列がその後必要ない場合は、インプレースバージョンの`bitpermute!`が推奨されます。

[`invbitpermute`](@ref)や[`bitpermute!`](@ref)も参照してください。
