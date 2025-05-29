```
testplot(model, args...; kwargs...)
```

Create a plot for test characteristics of `model`.

The resulting plot contains the test characteristic curve/expected scores (left) and the test information curve (right).

The additional `args...` and `kwargs...` are passed to the lower level plotting functions [`expected_score_plot`](@ref) and [`information_plot`](@ref).
