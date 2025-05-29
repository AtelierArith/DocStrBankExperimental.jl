```
cycle(f::QuadBin{ZZRingElem}; proper::Bool = false) -> Vector{QuadBin{ZZRingElem}}
```

`f`のサイクルをBuchmann–Vollmerによって定義されたように返します（アルゴリズム6.1）。サイクルは、`f`と`g`の最初の係数が同じ符号を持つすべての簡約された同値形`g`で構成されます。適切なサイクルはすべての同値形で構成され、サイクルと同じか2倍のサイズを持ちます。後者の場合、サイクルは奇数の長さを持ちます。
