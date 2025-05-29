```
induce_crt(L::Vector{PolyRingElem}, c::crt_env{ZZRingElem}) -> ZZPolyRingElem
```

ZZRingElem*poly 多項式 $L[i]$ と `crt*env`が与えられたとき、各係数に`crt` 関数を適用し、$f = L[i] \bmod p[i]$ という多項式を得ます。
