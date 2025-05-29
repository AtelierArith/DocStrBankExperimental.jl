```
swinnerton_dyer(n::Int, x::ZZPolyRingElem)
```

スウィンネルトン-ダイア多項式 $S_n$ を返します。これは整数多項式 $S_n = \prod (x \pm \sqrt{2} \pm \sqrt{3} \pm \sqrt{5} \pm \ldots \pm \sqrt{p_n})$ と定義され、ここで $p_n$ は $n$ 番目の素数を示し、すべての符号の組み合わせが取られます。この多項式の次数は $2^n$ であり、整数の範囲で既約です（これは $\sqrt{2} + \ldots + \sqrt{p_n}$ の最小多項式です）。
