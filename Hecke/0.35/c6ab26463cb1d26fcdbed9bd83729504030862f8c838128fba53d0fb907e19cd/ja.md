```
psi_upper(N::Integer, B::Int a::Int=771) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_upper(N::ZZRingElem, B::Int a::Int=771) -> Vector{Int}, ZZAbsPowerSeriesRingElem
```

バーンスタインのアイデアを使用しています: https://cr.yp.to/papers/psi.pdf を参照して、スムーズな数をカウントするpsi関数の上限を計算します。配列 $U$ が返され、$\psi(2^{i-1}, B) \ge U_i$ が成り立つようにします（$1\le i\le \rceil \log_2(B)\lceil$）。2つ目の返り値はバーンスタインの冪級数です。

オプションの他のパラメータ $a$ は結果の精度を制御し、デフォルトは771です。
