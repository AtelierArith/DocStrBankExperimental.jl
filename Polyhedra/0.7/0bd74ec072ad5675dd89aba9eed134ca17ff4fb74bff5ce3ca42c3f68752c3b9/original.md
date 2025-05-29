```
struct HalfSpace{T, AT} <: HRepElement{T, AT}
    a::AT
    β::T
end
```

An halfspace defined by the set of points $x$ such that $\langle a, x \rangle \le \beta$.
