```
Intersects{T} <: DE9IMPredicate{T}

Intersects(b)
Intersects()
```

`Intersects`: 2つのジオメトリが交差するのは、共通の点がある場合です。

`Intersects`述語は、2つのジオメトリが少なくとも1つの共通の点を持つ場合にtrueを返します。

`Intersects`が述語関数に渡されたオブジェクトをラップする場合、それは2番目の引数Bでなければなりません。
