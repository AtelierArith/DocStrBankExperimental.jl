```
transform_cost(cost, p0, tr::TransformationStructure; unames=nothing, pnames=nothing)
return DiffCost(new_cost, new_cost2), newp0
```

コスト関数 C(p) を与えると、新しい微分可能なコスト関数 D(q) を作成します。ここで、q = tr(p) であり、D(q) = C(p) です。
