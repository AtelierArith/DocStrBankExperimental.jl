```
Pipeline{name}(f)
```

Create a pipeline function with name. When calling the pipeline function, mark the result with `name`.  `f` should take two arguemnt: the input and a namedtuple (can be ignored) that the result will be  merged to. `name` can be either `Symbol` or tuple of `Symbol`s.

```
Pipeline{name}(f, n)
```

Create a pipline function with name. `f` should take one argument, it will be applied to either the input  or namedtuple depend on the value of `n`. `n` should be either `1` or `2`. Equivalent to  `f(n == 1 ? source : target)`.

```
Pipeline{name}(f, syms)
```

Create a pipline function with name. `syms` can be either a `Symbol` or a tuple of `Symbol`s.  Equivalent to `f(target[syms])` or `f(target[syms]...)` depends on the type of `syms`.

# Example

```julia-repl
julia> p = Pipeline{:x}(1) do x
           2x
       end
Pipeline{x}(var"#19#20"()(source))

julia> p(3)
(x = 6,)

julia> p = Pipeline{:x}() do x, y
           y.a * x
       end
Pipeline{x}(var"#21#22"()(source, target))

julia> p(2, (a=3, b=5))
(a = 3, b = 5, x = 6)

julia> p = Pipeline{:x}(y->y.a^2, 2)
Pipeline{x}(var"#23#24"()(target))

julia> p(2, (a = 3, b = 5))
(a = 3, b = 5, x = 9)

julia> p = Pipeline{(:sinx, :cosx)}(sincos, 1)
Pipeline{(sinx, cosx)}(sincos(source))

julia> p(0.5)
(sinx = 0.479425538604203, cosx = 0.8775825618903728)

julia> p = Pipeline{:z}((x, y)-> 2x+y, (:x, :y))
Pipeline{z}(var"#33#34"()(target.x, target.y))

julia> p(0, (x=3, y=5))
(x = 3, y = 5, z = 11)

```
