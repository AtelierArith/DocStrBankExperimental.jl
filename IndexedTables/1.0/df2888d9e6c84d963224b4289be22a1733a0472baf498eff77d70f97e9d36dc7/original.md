```
summarize(f, t, by = pkeynames(t); select = Not(by), stack = false, variable = :variable)
```

Apply summary functions column-wise to a table. Return a `NamedTuple` in the non-grouped case and a table in the grouped case. Use `stack=true` to stack results of the same summary function for different columns.

# Examples

```
using Statistics

t = table([1, 2, 3], [1, 1, 1], names = [:x, :y])

summarize((mean, std), t)
summarize((m = mean, s = std), t)
summarize(mean, t; stack=true)
summarize((mean, std), t; select = :y)
```
