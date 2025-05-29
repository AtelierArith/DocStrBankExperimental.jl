```
struct HyperPlane{T, AT} <: HRepElement{T, AT}
    a::AT
    β::T
end
```

An hyperplane defined by the set of points $x$ such that $\langle a, x \rangle = \beta$.
