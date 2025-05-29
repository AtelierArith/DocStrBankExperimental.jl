```
struct HalfSpace{T, AT} <: HRepElement{T, AT}
    a::AT
    β::T
end
```

点の集合によって定義される半空間 $x$ で、$\langle a, x \rangle \le \beta$ となります。
