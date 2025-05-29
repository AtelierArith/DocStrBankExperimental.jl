```
simplify(x::FacElem{QQFieldElem}) -> FacElem{QQFieldElem}
simplify(x::FacElem{ZZRingElem}) -> FacElem{ZZRingElem}
```

因子要素を簡素化します。すなわち、基数が互いに素になるように整列します。
