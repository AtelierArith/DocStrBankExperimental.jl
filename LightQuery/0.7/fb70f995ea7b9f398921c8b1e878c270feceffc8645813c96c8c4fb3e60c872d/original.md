```
macro _(body)
```

Terser function syntax. The arguments are inside the `body`; the first argument is `_`, the second argument is `__`, etc. Will `@inline`.

```jldoctest anonymous
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred (@_ _ + 1)(1)
2

julia> @inferred map((@_ __ - _), (1, 2), (2, 1))
(1, -1)
```

If there are no `_` arguments, read as is.

```jldoctest anonymous
julia> (@_ x -> x + 1)(1)
2
```
