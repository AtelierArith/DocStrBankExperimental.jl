```
restrict_dom!(f::BoundedQuadratic, dom::Interval)
restrict_dom!(f::BoundedQuadratic, lb::Real, ub::Real)
restrict_dom!(f::BoundedQuadratic, lb::Real, ub::Real, out::BoundedQuadratic)
```

`f`の定義域をインプレースで制限します。

参照: [`restrict_dom`](@ref)
