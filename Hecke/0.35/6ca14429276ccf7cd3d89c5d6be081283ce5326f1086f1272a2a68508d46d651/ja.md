```
psi_lower(N::Integer, B::Int, a::Int = 776) -> Vector{Int}, ZZAbsPowerSeriesRingElem
psi_lower(N::ZZRingElem, B::Int, a::Int = 776) -> Vector{Int}, ZZAbsPowerSeriesRingElem
```

バーンスタインのアイデアを使用しています: https://cr.yp.to/papers/psi.pdf を使用して、スムーズな数をカウントするpsi関数の下限を計算します。配列 $L$ が返され、$\psi(2^{i-1}, B) \ge L_i$ が成り立つようにします（$1\le i\le \rceil \log_2(B)\lceil$）。2つ目の返り値はバーンスタインの冪級数です。

オプションの他のパラメータ $a$ は結果の精度を制御し、デフォルトは776です。
