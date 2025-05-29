```
(approximations, radii) = mps_roots(coefficients, output_precision=53)
```

多項式の根を、その係数の配列によって指定された近似値を求めます。出力精度はビット単位で指定されます。

# 例

```jldoctest
julia> N = 64;

julia> cfs = zeros(Int, N + 1); cfs[end] = -(cfs[1] = 1);

julia> (app, rad) = mps_roots(cfs, 100);

julia> all(map(x->abs((x^N - 1)/(N*x^(N - 1))), app) < rad)
true
```
