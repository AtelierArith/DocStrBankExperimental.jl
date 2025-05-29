```
PrimesSet(f::Integer, t::Integer) -> PrimesSet
PrimesSet(f::ZZRingElem, t::ZZRingElem) -> PrimesSet
```

整数 $f$ と $t$ に対して、$f \le p \le t$ を満たす素数 $p$ を表す反復可能なオブジェクト $S$ を返します。$t=-1$ の場合、上限は無限です。
