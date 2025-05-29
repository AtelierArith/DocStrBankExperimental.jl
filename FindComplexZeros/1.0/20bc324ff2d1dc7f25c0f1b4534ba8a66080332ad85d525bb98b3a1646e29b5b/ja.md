```
countZeros(upper_left, lower_right, f::Function, increment=0.01, dif=0.5)::Int
```

与えられた長方形領域内の関数のゼロをカウントします

# 例

```julia-repl
julia> countZeros(-5 + 5im, 5 - 5im, x->(x - exp(1) * im)^3 * (x - exp(1))^2)
5
```
