```
SymFunction
```

シンボリック関数を作成するための型とコンストラクタ。これらのオブジェクトは、微分方程式を指定するために使用できます。マクロ [`@syms`](@ref) も `SymFunction` を構築するために利用可能です（`@syms f()`）。

## 例:

```jldoctest symfunction
julia> using SymPyPythonCall

julia> @syms t, v(); # シンボリック関数を作成するための推奨方法

julia> u = SymFunction("u") # 代替
u

julia> diff(v(t), t) |> show
Derivative(v(t), t)
```

## 拡張ヘルプ

`SymFunction` 型でラップされていないシンボリック関数の場合、`sympy.Function` コンストラクタを使用することができ、シンボリック関数を構築するために [`symbols`](@ref) 関数も使用できます（`F=sympy.Function("F", real=true)`; `F = sympy.symbols("F", cls=sympy.Function, real=true)`）。

```jldoctest symfunction
julia> @syms u(), v()::real, t
(u, v, t)

julia> sqrt(u(t)^2), sqrt(v(t)^2) # 実数値は異なる簡約規則を持つ
(sqrt(u(t)^2), Abs(v(t)))

```

このような関数は SymPy では未定義の関数であり、微分を取るなどのシンボリックに使用できます：

```jldoctest symfunction
julia> @syms x y u()
(x, y, u)

julia> diff(u(x), x) |> show
Derivative(u(x), x)

julia> diff(u(x, y), x) |> show
Derivative(u(x, y), x)
```

ここでは、`SymFunction` クラスと便利な `Differential` 関数を利用して、関数 `f` の逆関数の二次導関数を見つける方法の一例を示します：

```jldoctest symfunction
julia> @syms f() f⁻¹() x;

julia> D = Differential(x) # ∂(f) は diff(f(x),x)
Differential(x)

julia> D² = D∘D
Differential(x) ∘ Differential(x)

julia> u1 = only(solve(D((f⁻¹∘f)(x))  ~ 1, D(f⁻¹)(f(x)))); show(u1)
1/Derivative(f(x), x)

julia> u2 = only(solve(D²((f⁻¹∘f)(x)) ~ 0, D²(f⁻¹)(f(x)))); show(u2)
-Derivative(f(x), (x, 2))*Derivative(f⁻¹(f(x)), f(x))/Derivative(f(x), x)^2

julia> u2(D(f⁻¹)(f(x)) => u1) |> show # f''/[f']^3
-Derivative(f(x), (x, 2))/Derivative(f(x), x)^3
```
