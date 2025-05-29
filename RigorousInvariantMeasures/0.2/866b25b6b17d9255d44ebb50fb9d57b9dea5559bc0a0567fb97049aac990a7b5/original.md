```
value_and_derivative(f, x)
```

Evaluate f(x) and f'(x) at the same time.  We define a single method to do this because often there are shared subexpressions between a function and its derivatives, or they are computed together by automatic differentiation packages, so this is often more efficient than having two separate functions for f and f' and calling them separately.

The generic implementation uses `TaylorSeries` to compute derivatives. It can be overwritten for individual functions:

```
f = x -> x^2
value_and_derivative(f::typeof(f), x) = (x^2, 2x)
```

See @define*with*derivatives to define derivatives with three separate expressions.

Remark: when specializing derivatives by hand, always specialize the two-argoment functions  (e.g., `value_and_derivative(f, x)`) rather than the one-parameter ones  (e.g., `value_and_derivative(f)`), since the latter are defined generically in terms of the former.

Remark: tricky point that can cause subtle bugs: functions created in the same line-of-code will often have the same type; so for instance

# ```jldoctest

# julia> fs = [x -> k*x for k in 1:3];  # the three elements here have the same type

# julia> typeof(fs[1]) == typeof(fs[3])

# true

# julia> RigorousInvariantMeasures.derivative(f::typeof(fs[1]), x) = 1;

# julia> RigorousInvariantMeasures.derivative(f::typeof(fs[2]), x) = 2;

# julia> RigorousInvariantMeasures.derivative(f::typeof(fs[3]), x) = 3;

# julia> RigorousInvariantMeasures.derivative(fs[1], 0.5)  # this returns 3, not 1

# 3

# ```
