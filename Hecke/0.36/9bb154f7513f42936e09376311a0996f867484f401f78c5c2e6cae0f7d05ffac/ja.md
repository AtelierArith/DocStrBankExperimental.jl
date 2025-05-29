```
induce_crt(L::Vector{MatElem}, c::crt_env{ZZRingElem}) -> ZZMatrix
```

与えられた行列 $L[i]$ と `crt\_env` に対して、各係数に `crt` 関数を適用し、行列 $M = L[i] \bmod p[i]$ を得ます。
