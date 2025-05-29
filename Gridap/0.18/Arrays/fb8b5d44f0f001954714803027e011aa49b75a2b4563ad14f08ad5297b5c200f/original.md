```
lazy_map(f,a::AbstractArray...) -> AbstractArray
```

Applies the `Map` (or `Function`) `f` to the entries of the arrays in `a` (see the definition of [`Map`](@ref)).

The resulting array `r` is such that `r[i]` equals to `evaluate(f,ai...)` where `ai` is the tuple containing the `i`-th entry of the arrays in `a` (see function [`evaluate`](@ref) for more details). In other words, the resulting array is numerically equivalent to:

```
map( (x...)->evaluate(f,x...), a...)
```

# Examples

Using a function as mapping

```jldoctest
using Gridap.Arrays

a = collect(0:5)
b = collect(10:15)

c = lazy_map(+,a,b)

println(c)

# output
[10, 12, 14, 16, 18, 20]
```

Using a user-defined mapping

```jldoctest
using Gridap.Arrays
import Gridap.Arrays: evaluate!

a = collect(0:5)
b = collect(10:15)

struct MySum <: Map end

evaluate!(cache,::MySum,x,y) = x + y

k = MySum()

c = lazy_map(k,a,b)

println(c)

# output
[10, 12, 14, 16, 18, 20]
```
