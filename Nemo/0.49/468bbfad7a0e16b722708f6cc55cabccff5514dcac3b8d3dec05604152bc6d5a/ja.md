```
reconstruct(a::ZZRingElem, m::ZZRingElem, N::ZZRingElem, D::ZZRingElem)
```

有理数 $n/d$ を返そうとします。ここで、$0 \leq |n| \leq N$ かつ $0 < d \leq D$ であり、$2 N D < m$、gcd$(n, d) = 1$ かつ $a \equiv nd^{-1} \pmod{m}$ です。

戻り値はタプル (`success`, `n/d`) であり、`success` は再構築の成功を示します。

$$
a
$$

が負であるか $m$ より大きい場合、動作は未定義です。
