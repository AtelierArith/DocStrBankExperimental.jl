```
lll_with_removal_transform(x::ZZMatrix, b::ZZRingElem, ctx::LLLContext = LLLContext(0.99, 0.51))
```

ベクトルのノルムが上限 $b$ を超えるものを除去した後の LLL 簡約から残った最初の $r$ 行を持つタプル $(r, L, T)$ を計算します。ここで $T$ は $L = Tx$ となる変換行列です。
