```
univariate_maximize(f, a::Real, b::Real, transform, optimizer::GoldenSectionOpt, tol::Real)
```

`f(x)`を黄金分割法を使用して最大化します。`?golden_section_maximize`を参照してください。

# 例

```jldoctest
julia> f(x) = -(x-2)^2
f (generic function with 1 method)

julia> m = univariate_maximize(f, 1, 5, identity, GoldenSectionOpt(), 1e-10)
2.0000000000051843
```
