```
struct HyperPlane{T, AT} <: HRepElement{T, AT}
    a::AT
    β::T
end
```

点の集合によって定義されるハイパープレーン $x$ で、$\langle a, x \rangle = \beta$ となります。
