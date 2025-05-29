```
with_theme(f, theme = Theme(); kwargs...)
```

Calls `f` with `theme` temporarily activated. Attributes in `theme` can be overridden or extended with `kwargs`. The previous theme is always restored afterwards, no matter if `f` succeeds or fails.

Example:

```julia
my_theme = Theme(size = (500, 500), color = :red)
with_theme(my_theme, color = :blue, linestyle = :dashed) do
    scatter(randn(100, 2))
end
```
