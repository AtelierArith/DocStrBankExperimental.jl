```
doit
```

デフォルトでは評価されないオブジェクトを評価します。オブジェクトメソッドのエイリアスです。

## 拡張ヘルプ

例:

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

`deep=true`を設定すると、ネストされた式の評価を強制するために`doit`を再帰的に適用します:

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

`doit`のカリー形式もあります:

```jldoctest doit
julia> dfx |> doit
2⋅x

julia> dgfx |> doit(deep=true)
g(2⋅x)
```
