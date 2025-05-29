```
restrict_dom!(f::BoundedQuadratic, dom::Interval)
restrict_dom!(f::BoundedQuadratic, lb::Real, ub::Real)
restrict_dom!(f::BoundedQuadratic, lb::Real, ub::Real, out::BoundedQuadratic)
```

Restrict domain of `f` inplace.

See also: [`restrict_dom`](@ref)
