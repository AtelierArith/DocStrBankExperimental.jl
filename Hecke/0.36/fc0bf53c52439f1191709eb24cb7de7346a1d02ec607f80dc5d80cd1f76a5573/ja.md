```
quo(O::AbsSimpleNumFieldOrder, I::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbsSimpleNumFieldOrderQuoRing, Map
quo(O::AlgAssAbsOrd, I::AlgAssAbsOrdIdl) -> AbsOrdQuoRing, Map
```

商環 $O/I$ は環として、射影 $M: O\to O/I$ と共に存在します。$M$ の点ごとの逆は、前像/リフト関数を実装します。一般に、これは線形ではないため、セクションにはなりません。
