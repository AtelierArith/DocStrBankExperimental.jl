```
insert!(ir, v, x)
```

Insert the expression or statement `x` into the given IR, just before the variable `v` is defined, returning the new variable for `x`. See also [`insertafter!`](@ref).

```
julia> f(x) = 3x + 2
f (generic function with 1 method)

julia> ir = @code_ir f(1)
1: (%1, %2)
  %3 = 3 * %2
  %4 = %3 + 2
  return %4

julia> insert!(ir, IRTools.var(4), :(println("hello, world")))
%5

julia> ir
1: (%1, %2)
  %3 = 3 * %2
  %5 = println("hello, world")
  %4 = %3 + 2
  return %4
```
