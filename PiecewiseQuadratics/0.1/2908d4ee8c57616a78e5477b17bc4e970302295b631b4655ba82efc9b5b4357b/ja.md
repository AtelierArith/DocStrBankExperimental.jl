```
PiecewiseQuadratic()
PiecewiseQuadratic(f::BoundedQuadratic)
PiecewiseQuadratic(f_list::Vector{BoundedQuadratic}[; simplify_result=false])
```

区分的二次関数を表し、各部分は `BoundedQuadratic` です。

フィールドは次のことを表します：

  * `f_list`: `BoundedQuadratic` 関数の `Vector`

# 例

```jldoctest
julia> left = BoundedQuadratic(-Inf, 0., 0., -1., 0.)
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]

julia> right = BoundedQuadratic(0., Inf, 0., 1., 0.)
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

julia> pwq = PiecewiseQuadratic([left, right])
区分的二次関数:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

```
