```
sum(f_list::Vector{BoundedQuadratic})
```

有効な場合は、BoundedQuadraticのリストのBoundedQuadraticの合計を返し、そうでない場合は`nothing`を返します。

# 例

```jldoctest
julia> bq = BoundedQuadratic(-1., 5., 1., 2., 3.)
BoundedQuadratic: f(x) = 1.00000 x² + 2.00000 x + 3.00000, ∀x ∈ [-1.00000, 5.00000]

julia> sum([bq, bq])
BoundedQuadratic: f(x) = 2.00000 x² + 4.00000 x + 6.00000, ∀x ∈ [-1.00000, 5.00000]

```
