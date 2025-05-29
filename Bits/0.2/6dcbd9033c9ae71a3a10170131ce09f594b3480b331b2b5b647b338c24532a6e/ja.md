```
bitsize(T::Type) -> Int
bitsize(::T)     -> Int
```

型 `T` が保持できるビット数を返します。ビット数が動的な値（例えば `BitFloat` のような）である場合のみ、2 番目のメソッドを定義できます。

# 例

```jldoctest
julia> bitsize(Int32)  == 32        &&
       bitsize(true)   == 1         &&
       bitsize(big(0)) == Bits.INF  &&
       bitsize(1.2)    == 64
true

julia> x = big(1.2); bitsize(x) == 256 + sizeof(x.exp)*8 + 1
true
```
