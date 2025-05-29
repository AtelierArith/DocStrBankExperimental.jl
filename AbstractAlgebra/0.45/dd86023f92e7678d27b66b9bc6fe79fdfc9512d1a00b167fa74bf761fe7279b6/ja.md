```
deflate(f::MPolyRingElem{T}, defl::Vector{Int}) where T <: RingElement
```

与えられた指数（各変数に対して1つの減衰因子の配列として供給される）で除算された同じ係数を持つ多項式を返します。

アルゴリズムは、$0$の減衰を$1$に自動的に置き換え、$0$での除算を回避します。
