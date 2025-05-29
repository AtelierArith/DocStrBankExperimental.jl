```
zz2vector!(a::ZZ2Vector, n) -> a
```

`a`を`n`のビット表現で埋めて、`a`を返します。ここで、`n`は`Base.BitInteger`または`BitIntegers.jl`パッケージによって定義されたビット整数でなければなりません。`a`の長さは`n`のビット長に設定されます。

関連情報としては、[`zz2vector`](@ref)、`Base.BitInteger`、`BitIntegers.AbstractBitSigned`、`BitIntegers.AbstractBitUnsigned`があります。
