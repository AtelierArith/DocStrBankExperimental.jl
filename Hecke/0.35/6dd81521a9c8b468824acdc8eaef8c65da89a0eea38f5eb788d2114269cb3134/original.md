```
simplify(x::FacElem{QQFieldElem}) -> FacElem{QQFieldElem}
simplify(x::FacElem{ZZRingElem}) -> FacElem{ZZRingElem}
```

Simplfies the factored element, i.e. arranges for the base to be coprime.
