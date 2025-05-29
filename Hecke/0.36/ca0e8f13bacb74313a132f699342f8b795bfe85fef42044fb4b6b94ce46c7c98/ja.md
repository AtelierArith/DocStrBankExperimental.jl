```
localization(OK::AbsNumFieldOrder{AbsSimpleNumField,T}, S::AbsNumFieldOrderIdeal{AbsSimpleNumField,T}; cached=true, comp = false) where {T <: AbsSimpleNumFieldElem}
```

$$
OK
$$

のイデアル $S$ における局所化を返します。`cached == true`（デフォルト）であれば、結果の局所化親オブジェクトはキャッシュされ、同じ順序 $OK$ とイデアル $S$ を持つコンストラクタへのその後の呼び出しに対して返されます。`comp == false` は $S$ を割る素数が可逆であることを意味し、`comp == true` は $S$ を割らないすべての素数が単位になることを意味します。
