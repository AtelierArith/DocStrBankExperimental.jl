黄金比探索法。

関数 f が区間 [a,b] に単一の局所最小値を持つとき、gss は最小値を含む部分区間 [c,d] を返します。ただし、d-c <= tol です。

# 例

```jldoctest
julia> f(x) = -(x-2)^2
f (generic function with 1 method)

julia> m = golden_section_maximize(f, 1, 5, identity, 1e-10)
2.0000000000051843
```

出典: https://en.wikipedia.org/wiki/Golden-section_search
