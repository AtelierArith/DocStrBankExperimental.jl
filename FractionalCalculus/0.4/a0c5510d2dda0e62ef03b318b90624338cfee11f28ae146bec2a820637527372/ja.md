# グリュンワルト・レティニコフ意味の有限差分近似

```
fracdiff(f::Union{Function, Number}, α::AbstractArray, end_point, h, ::GLFiniteDifference)::Vector
```

有限差分法を使用してグリュンワルト・レティニコフ意味の分数導関数を取得します。

### 例

```julia-repl
julia> fracdiff(x->x, 0.5, 1, 0.01, GLFiniteDifference())
1.1269695801851276
```
