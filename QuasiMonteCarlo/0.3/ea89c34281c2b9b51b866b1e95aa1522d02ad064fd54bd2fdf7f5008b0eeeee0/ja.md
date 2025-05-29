```
GoldenSample()
```

一般化された黄金比の累乗を使用して、準ランダムなクロネッカー列を生成します。

調和的または一般化された黄金比は、次の方程式の解として定義されます: $x^d = x + 1$

ここで `d` は列の次元です。黄金列は、`Kronecker([x^-i for i in 1:d])` と同等です。

警告: 2次元を超える一般化された黄金列は純粋に実験的です。高次元では不均一性が悪い可能性があり、より良く知られた準ランダム列に対して答えを検証せずに使用すべきではありません。代わりにランク1の格子法を試してください。

参考文献: Roberts, M. (2018). The Unreasonable Effectiveness of Quasirandom Sequences. *Extreme Learning.* http://extremelearning.com.au/unreasonable-effectiveness-of-quasirandom-sequences/
