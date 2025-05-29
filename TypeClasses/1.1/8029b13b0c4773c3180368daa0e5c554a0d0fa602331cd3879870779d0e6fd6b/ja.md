```
orelse(d1::Dict, d2::Dict) -> Dict
```

Option値に関するorelseのセマンティクスに従い、最初の値が保持され、2番目の値は破棄されます。したがって、これは`Base.merge`の反転バージョンです。
