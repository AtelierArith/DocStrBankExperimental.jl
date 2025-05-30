```
struct Line{T, AT <: AbstractVector{T}}
    a::AT
end
```

`a` と `-a` の円錐包、すなわち `λa` の点の集合であり、ここで `λ` は任意の実数です。
