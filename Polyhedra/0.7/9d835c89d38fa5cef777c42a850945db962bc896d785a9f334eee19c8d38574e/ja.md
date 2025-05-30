```
struct Ray{T, AT <: AbstractVector{T}}
    a::AT
end
```

`a`の円錐包、すなわち、`λ`が任意の非負実数であるときの点`λa`の集合。
