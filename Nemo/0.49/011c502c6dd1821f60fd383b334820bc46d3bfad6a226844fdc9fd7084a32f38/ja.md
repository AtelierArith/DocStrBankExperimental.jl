```
lll_with_removal(x::ZZMatrix, b::ZZRingElem, ctx::LLLContext = LLLContext(0.99, 0.51))
```

行列 $x$ の LLL 削減を計算し、与えられた上限 $b$ を超えるノルムを持つ行を捨てます。戻り値はタプル $(r, L)$ で、$L$ の最初の $r$ 行は削除後に残った行です。
