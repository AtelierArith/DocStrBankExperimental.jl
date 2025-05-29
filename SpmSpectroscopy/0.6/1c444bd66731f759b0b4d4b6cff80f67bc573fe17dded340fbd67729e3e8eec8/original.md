```
correct_background!(xdata::AbstractVector{<:Real}, ydata::AbstractVector{<:Real}, type::Background, offset::Bool=true)::Nothing
```

Background correction of `ydata` vs. `xdata` with using a correction of type `type`. If `offset` is `true` (default), then `ydata` will be shifted such that its minimum is 0.
