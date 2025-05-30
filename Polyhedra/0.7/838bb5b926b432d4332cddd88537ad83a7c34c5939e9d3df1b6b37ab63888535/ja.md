```
struct Line{T, AT <: AbstractVector{T}}
    a::AT
end
```

ベクトル `a` と `-a` の円錐包、すなわち、任意の実数 `λ` に対する点 `λa` の集合。
