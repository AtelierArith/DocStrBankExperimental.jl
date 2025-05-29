```
vtcounteq(x::AbstractArray, y::AbstractArray; dims=:)
```

`xᵢ == yᵢ` が `true` を返す要素の数を、次元 `dims` に沿ったスライスに対応するベクトルでカウントします。スレッド対応。

参照: [`vtcountne`](@ref)
