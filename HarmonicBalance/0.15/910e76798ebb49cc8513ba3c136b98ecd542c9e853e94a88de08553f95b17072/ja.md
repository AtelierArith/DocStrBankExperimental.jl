```julia
get_krylov_equations(
    diff_eom::QuestBase.DifferentialEquation;
    order,
    fast_time,
    slow_time
)

```

特定の `order` に対してKrylov-Bogoliubov平均化法を適用し、`diff_eom` の調和を支配する一連のODE（スローフロー方程式）を取得します。

調和は `slow_time` で進化し、振動項自体は `fast_time` で進化します。入力がない場合、変数 T が `slow_time` に定義され、`fast_time` は `diff_eom` の独立変数として取られます。

Krylov-Bogoliubov平均化法は `order = 2` まで適用できます。

# 例

```julia-repl
julia> @variables t, x(t), ω0, ω, F;

# 単純調和振動子を入力
julia> diff_eom = DifferentialEquation( d(x,t,2) + ω0^2 * x ~ F *cos(ω*t), x);

# 調和ωでxを展開
julia> add_harmonic!(diff_eom, x, ω);

# スロウタイムTで進化する調和の方程式を1次で取得
julia> harmonic_eom = get_krylov_equations(diff_eom, order = 1)

一連の2つの調和方程式
変数: u1(T), v1(T)
パラメータ: ω, F, ω0

調和アプローチ:
xˍt(t) =
x(t) = u1(T)*cos(ωt) + v1(T)*sin(ωt)

調和方程式:

((1//2)*(ω^2)*v1(T) - (1//2)*(ω0^2)*v1(T)) / ω ~ Differential(T)(u1(T))

((1//2)*(ω0^2)*u1(T) - (1//2)*F - (1//2)*(ω^2)*u1(T)) / ω ~ Differential(T)(v1(T))
```
