```
solve!(cb, solver, b; kwargs...)
```

`cb`を`solve!`のコールバックとして渡します。

# 例

```julia
julia> x_approx = solve!(solver, b) do solver, iteration
  println(iteration)
end
```
