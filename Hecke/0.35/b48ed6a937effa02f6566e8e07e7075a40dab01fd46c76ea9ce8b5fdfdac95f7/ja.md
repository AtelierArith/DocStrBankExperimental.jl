```
tates_algorithm_local(E::EllipticCurve{AbsSimpleNumFieldElem}, p:: AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem})
-> EllipticCurve{AbsSimpleNumFieldElem}, String, ZZRingElem, ZZRingElem, Bool
```

タプル $(\tilde E, K, m, f, c, s)$ を返します。ここで、$\tilde E$ は素イデアル $p$ における $E$ の最小モデル、$K$ は小平記号、$f$ は $p$ における導関数の評価、$c$ は $p$ における局所タマガワ数であり、`s` は $E$ が非分割の乗法的縮小を持つ場合に限り偽です。
