```
struct Line{T, AT <: AbstractVector{T}}
    a::AT
end
```

`a` と `-a` の円錐包、すなわち、任意の実数である `λ` に対して `λa` となる点の集合。
