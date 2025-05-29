```
evaluate(a, [vals]; sorting::Bool=true)
```

Evaluate the `TaylorN` polynomial `a` at `vals`. If `vals` is omitted, it's evaluated at zero. The keyword parameter `sorting` can be used to avoid sorting (in increasing order by `abs2`) the terms that are added.

Note that the syntax `a(vals)` is equivalent to `evaluate(a, vals)`; and `a()` is equivalent to `evaluate(a)`; use a(b::Bool, x) corresponds to evaluate(a, x, sorting=b).
