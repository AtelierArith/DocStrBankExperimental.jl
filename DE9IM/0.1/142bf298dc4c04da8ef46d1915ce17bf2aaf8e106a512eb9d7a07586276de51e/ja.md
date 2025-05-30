```
CoveredBy{T} <: DE9IMPredicate{T}

CoveredBy(b)
CoveredBy()
```

`CoveredBy`: 幾何学Aは幾何学Bによって覆われているのは、AとBの交差がAに等しい場合に限ります。

`CoveredBy`述語は、2つの幾何学の交差が最初の幾何学に等しい場合にtrueを返します。

`CoveredBy`が述語関数に渡されたオブジェクトをラップしている場合、それは2番目の引数Bでなければなりません。
