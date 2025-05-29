```
boxconstraints(lb, ub, [rigid])
BoxConstrainedSpace(ub, lb, [rigid])
```

ボックス制約付き探索空間を定義します（BoxConstrainedSpaceのエイリアス）。

詳細については[`SearchSpaces.BoxConstrainedSpace`](@ref)を参照してください。

# 例

```julia
f(x) = (x[1] - 100)^2 + sum(abs.(x[2:end]))
bounds = boxconstraints(lb = zeros(5), ub = ones(5), rigid = false)
optimize(f, bounds, ECA)
```
