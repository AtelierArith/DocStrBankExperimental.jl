```
vtcountne(x::AbstractArray, y::AbstractArray; dims=:)
```

`xᵢ != yᵢ` が `true` を返す要素の数をカウントします。これは、次元 `dims` に沿ったスライスに対応するベクトルで行われます。スレッド対応です。

参照: [`vtcounteq`](@ref)
