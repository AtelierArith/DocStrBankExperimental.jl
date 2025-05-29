```
zz2vector(n) -> ZZ2Vector
```

`n`のビット表現を含む`ZZ2Vector`を返します。ここで、`n`は`Base.BitInteger`または`BitIntegers.jl`パッケージによって定義されたビット整数でなければなりません。

関連情報としては、[`zz2vector!`](@ref)、`Base.BitInteger`、`BitIntegers.AbstractBitSigned`、`BitIntegers.AbstractBitUnsigned`があります。

# 例

```jldoctest
julia> zz2vector(Int8(35))
8-element ZZ2Vector:
 1
 1
 0
 0
 0
 1
 0
 0
```
