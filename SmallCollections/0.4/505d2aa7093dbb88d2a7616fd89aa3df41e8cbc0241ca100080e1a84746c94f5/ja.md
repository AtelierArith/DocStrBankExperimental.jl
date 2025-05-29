```
SmallCollections.bitsize(T::Type) -> Int
SmallCollections.bitsize(x::T) where T -> Int
```

`T`の内部バイナリ表現のサイズをビット単位で返します。`Bool`の場合、関数は`1`を返します。

`Base.sizeof`も参照してください。
