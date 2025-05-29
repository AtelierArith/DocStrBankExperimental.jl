```
is_convex(f::PiecewiseQuadratic)
```

`f` が凸であれば `true` を返します。

`PiecewiseQuadratic` は、すべての `i` に対して以下の条件を満たす場合に凸です：

  * `f_i` は凸である
  * `f_i.ub == f_{i+1}.lb`
  * `derivative(f_i)(f_i.ub) <= derivative(f_{i+1})(f_{i+1}.lb)`

# 例

```jldoctest
julia> left = BoundedQuadratic(-Inf, 0., 0., -1., 0.)
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]

julia> right = BoundedQuadratic(0., Inf, 0., 1., 0.)
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

julia> pwq = PiecewiseQuadratic([left, right])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-Inf, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, Inf]

julia> is_convex(pwq)
true

```
