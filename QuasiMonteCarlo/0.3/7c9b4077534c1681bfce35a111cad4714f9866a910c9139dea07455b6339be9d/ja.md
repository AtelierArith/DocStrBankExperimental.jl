```
FaureSample(R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

ファウレ低不均一性列。

ファウレ分布サンプルは、すべての変数に対して同じ点のセットを使用し、順序を考慮してすべての次元を均等にカバーします。

スクランブルされた場合、ランダム化されたファウレ列は、分散が純粋なモンテカルロ積分の最大 `exp(1) ≈ 2.718` 倍になるという最悪の場合の保証を提供します。しかし、低い有効次元を持つ関数（最初のいくつかの入力が評価を支配する関数）を積分する際には、ソボル列よりもはるかに効率が悪いです。

次元 `s` のファウレ列は、基数 `b = nextprime(s)` を持つ `(0, s)`-列を形成します。

ファウレ列は、長さ `k * base^s` を持ち、`k < base < 1` でなければなりません。

参考文献: Faure, H. (1982). Discrépance de suites associées à un système de numération (en dimension s). *Acta Arith.*, 41, 337-351. Owen, A. B. (1997). Monte Carlo variance of scrambled net quadrature. *SIAM Journal on Numerical Analysis*, 34(5), 1884-1910.
