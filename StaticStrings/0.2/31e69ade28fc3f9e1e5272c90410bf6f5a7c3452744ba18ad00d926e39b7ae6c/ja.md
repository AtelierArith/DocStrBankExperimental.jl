```
CStaticString(data::NTuple{N,UInt8})
cstatic"string"N
```

[`AbstractStaticString`](@ref) は、NTuple{N,UInt8} にコードユニットを格納しますが、NUL コードユニットは末尾にある必要があります。

`String` に変換すると、ヌルバイトが含まれます。ヌルバイトなしの `SubString` を取得するには `strip` を使用してください。

注: `CStaticString{N}` のサイズは `N+1` バイトです。
