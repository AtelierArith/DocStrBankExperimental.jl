`subs` は、式内の値を別の値に置き換えるために使用されます。例：

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

`subs` のカリー形式は、チェイニング `|>` 演算子と一緒に使用するためのものです。

```jldoctest subs
julia> ex |> subs(x,ℯ)
(ℯ - y)⋅(2⋅y + ℯ)
```

ペアを使用することで便利な代替手段が得られます：

```jldoctest subs
julia> subs(ex, x=>1, y=>2)
-5

julia> ex |> subs(x=>1, y=>2)
-5
```
