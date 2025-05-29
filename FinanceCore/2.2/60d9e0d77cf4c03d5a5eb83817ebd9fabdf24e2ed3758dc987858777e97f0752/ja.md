```
rate(r::Rate)
```

`Rate`によって表される型なしスカラー金利を返します。

# 例

```julia-repl
julia> r =Continuous(0.03)
Yields.Rate{Float64, Continuous}(0.03, Continuous())

julia> rate(r)
0.03
```
