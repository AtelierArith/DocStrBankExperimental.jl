```julia
get_harmonic_equations(
    diff_eom::QuestBase.DifferentialEquation;
    fast_time,
    slow_time,
    degree,
    jacobian
) -> QuestBase.HarmonicEquation

```

ハーモニックアンサッツを適用し、続いてスローフロー、フーリエ変換を行い、高次の導関数を省略して、`diff_eom`のハーモニクスを支配する一連のODE（ハーモニック方程式）を得ます。

ハーモニクスは`slow_time`で進化し、振動する項自体は`fast_time`で進化します。入力がない場合、変数Tが`slow_time`のために定義され、`fast_time`は`diff_eom`の独立変数として取られます。

デフォルトでは、`slow_time`の導関数の次数が1を超えるすべての積は省略されるため、方程式は時間導関数に対して線形になります。

# 例

```julia-repl
julia> @variables t, x(t), ω0, ω, F;

# 単純な調和振動子を入力
julia> diff_eom = DifferentialEquation( d(x,t,2) + ω0^2 * x ~ F *cos(ω*t), x);

# ハーモニックωでxを展開
julia> add_harmonic!(diff_eom, x, ω);

# スロウタイムTで進化するハーモニクスの方程式を取得
julia> harmonic_eom = get_harmonic_equations(diff_eom)

一連の2つのハーモニック方程式
変数: u1(T), v1(T)
パラメータ: ω0, ω, F

ハーモニックアンサッツ:
x(t) = u1*cos(ωt) + v1*sin(ωt)

ハーモニック方程式:

(ω0^2)*u1(T) + (2//1)*ω*Differential(T)(v1(T)) - (ω^2)*u1(T) ~ F

(ω0^2)*v1(T) - (ω^2)*v1(T) - (2//1)*ω*Differential(T)(u1(T)) ~ 0
```
