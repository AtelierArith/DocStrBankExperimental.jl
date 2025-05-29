```
PrimesSet(f::Integer, t::Integer, mod::Integer, val::Integer)
PrimesSet(f::ZZRingElem, t::ZZRingElem, mod::ZZRingElem, val::ZZRingElem)
```

返されるのは、$f \le p \le t$ かつ $p\equiv val \bmod mod$ を満たす素数 $p$ を表す反復可能なオブジェクト $S$ です（算術級数における素数）。もし $t=-1$ の場合、上限は無限です。
