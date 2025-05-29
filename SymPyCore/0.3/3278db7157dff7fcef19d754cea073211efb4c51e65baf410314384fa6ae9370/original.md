`subs` is used to substitute a value in an expression with another value. Examples:

```jldoctest subs
julia> using SymPyPythonCall



julia> @syms x,y
(x, y)

julia> ex = (x-y)*(x+2y)
(x - y)⋅(x + 2⋅y)

julia> subs(ex, (y, y^2)) |> show
(x - y^2)*(x + 2*y^2)

julia> subs(ex, (x,1), (y,2))
-5

julia> subs(ex, (x,y^3), (y,2))
72

julia> subs(ex, y, 3)
(x - 3)⋅(x + 6)
```

There is a curried form of `subs` to use with the chaining `|>` operator

```jldoctest subs
julia> ex |> subs(x,ℯ)
(ℯ - y)⋅(2⋅y + ℯ)
```

The use of pairs gives a convenient alternative:

```jldoctest subs
julia> subs(ex, x=>1, y=>2)
-5

julia> ex |> subs(x=>1, y=>2)
-5
```
