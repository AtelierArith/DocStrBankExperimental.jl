```
induce_rational_reconstruction(a::ZZPolyRingElem, M::ZZRingElem) -> QQPolyRingElem
```

各係数に `rational_reconstruction` を適用し、失敗した場合は (false, s.th.) を返すか、成功した場合は (true, g) を返します。ここで、$g$ は $g \equiv a \bmod M$ を満たす有理多項式です。
