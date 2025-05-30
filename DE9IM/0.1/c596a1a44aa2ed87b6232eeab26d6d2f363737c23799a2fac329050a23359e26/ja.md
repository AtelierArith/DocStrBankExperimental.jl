```
Contains{T} <: DE9IMPredicate{T}

Contains(b)
Contains()
```

`Contains`: 幾何学Aは幾何学Bを含むのは、Bのすべての点がAの内部にある場合に限ります。

`Contains`述語は、2番目の幾何学のすべての点が最初の幾何学の内部にある場合にtrueを返します。

`Contains`が述語関数に渡されたオブジェクトをラップする場合、それは2番目の引数Bでなければなりません。
