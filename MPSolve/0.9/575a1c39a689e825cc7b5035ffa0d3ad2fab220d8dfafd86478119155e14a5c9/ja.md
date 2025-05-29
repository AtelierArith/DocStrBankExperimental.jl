```
(approximations, radii) = mps_roots(A, B, output_precision=53)
```

世俗方程の根を近似します。出力精度はビット単位で指定されます。

# 例

```jldoctest
julia>  S(x) = 1/(x - 2) + 3/(x - 4) + 5/(x - 6) - 1;

julia> rt,rad=mps_roots([1, 3, 5],[2, 4, 6]);

julia> rtb,radb=mps_roots([1, 3, 5],[2, 4, 6],output_precision=256);

julia> all(abs.(rt-rtb) .< max.(rad,abs.(rtb)*eps()))
true

```
