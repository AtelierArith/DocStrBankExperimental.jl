```
Operation(op)
```

Returns the map that results after applying an operation `f` over a set of map(s) `args`. That is `Operation(f)(args)(x...)` is formally defined as `f(map(a->a(x...),args)...)`.

# Example

```jldoctest
using Gridap.Arrays

fa(x) = x.*x
fb(x) = sqrt.(x)

x = collect(0:5)

fab = Operation(fa)(fb)
c = evaluate(fab,x)

println(c)

# output
[0.0, 1.0, 2.0, 3.0, 4.0, 5.0]
```
