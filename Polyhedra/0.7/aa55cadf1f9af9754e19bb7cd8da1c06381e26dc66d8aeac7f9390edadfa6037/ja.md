```
removehredundancy!(p::HRep; kws...)
```

`p`のH表現の要素を削除します。これは、`p`が表す多面体を変更することなく削除できる要素です。つまり、多面体の面に対応する半空間のみを保持します。

残りのキーワード引数`kws`は、[`detectvlinearity!`](@ref)および[`detecthlinearity!`](@ref)に渡されます。
