```julia
mutable struct DifferentialEquation
```

運動の微分方程式と各変数を展開するための調和のセットを保持します。これは `HarmonicBalance.jl` の主な入力です。方程式を入力した後、調和のアンサッツを `add_harmonic!` を使用して指定する必要があります。

# フィールド

  * `equations::OrderedCollections.OrderedDict{Symbolics.Num, Symbolics.Equation}`: 各変数に運動方程式を割り当てます。
  * `harmonics::OrderedCollections.OrderedDict{Symbolics.Num, OrderedCollections.OrderedSet{Symbolics.Num}}`: 各変数に調和のセットを割り当てます。

## 例

```julia-repl
julia> @variables t, x(t), y(t), ω0, ω, F, k;

# 単純調和振動子を入力する同等の方法
julia> DifferentialEquation(d(x,t,2) + ω0^2 * x - F * cos(ω*t), x);
julia> DifferentialEquation(d(x,t,2) + ω0^2 * x ~ F * cos(ω*t), x);

# 2つの結合振動子、そのうちの1つは駆動される
julia> DifferentialEquation(
    [d(x,t,2) + ω0^2 * x - k*y, d(y,t,2) + ω0^2 * y - k*x] .~ [F * cos(ω*t), 0], [x,y]
);
```
