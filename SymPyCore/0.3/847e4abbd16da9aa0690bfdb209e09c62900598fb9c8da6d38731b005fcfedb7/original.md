```
doit
```

Evaluates objects that are not evaluated by default. Alias for object method.

## Extended help

Examples:

```jldoctest doit
julia> using SymPyPythonCall

julia> @syms x f()
(x, f)

julia> D = Differential(x)
Differential(x)

julia> df = D(f(x)); show(df)
Derivative(f(x), x)

julia> dfx = subs(df, (f(x), x^2));  show(dfx)
Derivative(x^2, x)

julia> doit(dfx)
2⋅x
```

Set `deep=true` to apply `doit` recursively to force evaluation of nested expressions:

```jldoctest doit
julia> @syms g()
(g,)

julia> dgfx = g(dfx);  show(dgfx)
g(Derivative(x^2, x))

julia> doit(dgfx) |> show
g(Derivative(x^2, x))

julia> doit(dgfx, deep=true)
g(2⋅x)
```

There is also a curried form of `doit`:

```jldoctest doit
julia> dfx |> doit
2⋅x

julia> dgfx |> doit(deep=true)
g(2⋅x)
```
