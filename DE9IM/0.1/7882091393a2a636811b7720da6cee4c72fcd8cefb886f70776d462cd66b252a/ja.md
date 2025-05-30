```
Disjoint{T} <: DE9IMPredicate{T}

Disjoint(b)
Disjoint()
```

`Disjoint`: 2つのジオメトリが離散しているとは、それらの交差が空であることを意味します。

`Disjoint`述語は、2つのジオメトリが共通の点を持たない場合に真を返します。

`Disjoint`が述語関数に渡されたオブジェクトをラップする場合、それは2番目の引数Bでなければなりません。
