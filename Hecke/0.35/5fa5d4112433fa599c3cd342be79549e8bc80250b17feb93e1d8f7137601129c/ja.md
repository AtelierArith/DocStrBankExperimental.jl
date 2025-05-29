```
tates_algorithm_local(E::EllipticCurve{QQFieldElem}, p:: Int)
-> elliptic_curve{QQFieldElem}, String, ZZRingElem, ZZRingElem, Bool
```

タプル $(\tilde E, K, f, c, s)$ を返します。ここで、$\tilde E$ は素イデアル $p$ における $E$ の最小モデル、$K$ は小平記号、$f$ は $p$ における導関数の評価、$c$ は $p$ における局所タマガワ数、$s$ は $E$ が非分割乗法的縮小を持つ場合に限り偽です。
