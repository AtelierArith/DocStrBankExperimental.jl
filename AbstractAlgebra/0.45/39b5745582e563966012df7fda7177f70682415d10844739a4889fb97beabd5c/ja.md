```
deflation(p::PolyRingElem)
```

タプル `(shift, defl)` を返します。ここで `shift` は $p$ の末尾項の指数であり、`defl` は $p$ の非ゼロ項の指数間の距離の gcd です。もし $p = 0$ であれば、`shift` と `defl` の両方はゼロになります。
