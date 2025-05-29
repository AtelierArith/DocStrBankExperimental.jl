```
dsolve(eqn, var, args..,; ics=nothing, kwargs...)
```

`sympy.dsolve`を呼び出します。

ics: 初期条件は辞書または`nothing`で指定されます。

# 拡張ヘルプ

例:

```jldoctest dsolve
julia> using SymPyPythonCall

julia> @syms α, x, f(), g()
(α, x, f, g)

julia> ∂ = Differential(x)
Differential(x)

julia> eqn = ∂(f(x)) ~ α * x; show(eqn)
Eq(Derivative(f(x), x), x*α)
```

```jldoctest dsolve
julia> dsolve(eqn) |> show
Eq(f(x), C1 + x^2*α/2)
```

```julia jldoctest dsolve
julia> dsolve(eqn(α=>2); ics=Dict(f(0)=>1))
        2
f(x) = x  + 1

julia> eqn = ∂(∂(f(x))) ~ -f(x);

julia> dsolve(eqn)
f(x) = C₁⋅sin(x) + C₂⋅cos(x)

julia> dsolve(eqn; ics = Dict(f(0)=>1, ∂(f)(0) => -1))
f(x) = -sin(x) + cos(x)

julia> eqn = ∂(∂(f(x))) - f(x) - exp(x);

julia> dsolve(eqn, ics=Dict(f(0) => 1, f(1) => Sym(1//2))) |> show
Eq(f(x), (x/2 + (-exp(2) - 2 + E)/(-2 + 2*exp(2)))*exp(x) + (-E + 3*exp(2))*exp(-x)/(-2 + 2*exp(2)))
```

!!! note "システム"
    複数の方程式がある場合は、ベクトルではなくタプルを使用してください。


```julia jldoctest dsolve
julia> @syms x() y() t g
(x, y, t, g)

julia> ∂ = Differential(t)
Differential(t)

julia> eqns = (∂(x(t)) ~ y(t), ∂(y(t)) ~ x(t));

julia> dsolve(eqns)
2-element Vector{Sym{PythonCall.Py}}:
 Eq(x(t), -C1*exp(-t) + C2*exp(t))
  Eq(y(t), C1*exp(-t) + C2*exp(t))

julia> dsolve(eqns, ics = Dict(x(0) => 1, y(0) => 2))
2-element Vector{Sym{PythonCall.Py}}:
 Eq(x(t), 3*exp(t)/2 - exp(-t)/2)
 Eq(y(t), 3*exp(t)/2 + exp(-t)/2)

julia> eqns = (∂(∂(x(t))) ~ 0, ∂(∂(y(t))) ~ -g)
(Eq(Derivative(x(t), (t, 2)), 0), Eq(Derivative(y(t), (t, 2)), -g))

julia> dsolve(eqns)  # 初期条件に対しては解けません！(NotAlgebraic)
2-element Vector{Sym{PythonCall.Py}}:
           x(t) = C₁ + C₂⋅t
 Eq(y(t), C3 + C4*t - g*t^2/2)

julia> @syms t x() y()
(t, x, y)

julia> eq = (∂(x)(t) ~ x(t)*y(t)*sin(t), ∂(y)(t) ~ y(t)^2 * sin(t));
```

```julia
julia> dsolve(eq)
Set{Sym{PythonCall.Py}} with 2 elements:
  Eq(x(t), -exp(C1)/(C2*exp(C1) - cos(t)))
  Eq(y(t), -1/(C1 - cos(t)))
```
