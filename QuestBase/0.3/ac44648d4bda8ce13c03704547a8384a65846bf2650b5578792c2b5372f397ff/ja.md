```julia
add_harmonic!(
    diff_eom::QuestBase.DifferentialEquation,
    var::Symbolics.Num,
    ω
)

```

ハーモニック `ω` を `diff_eom` 内の変数 `var` を展開するために使用されるハーモニックアンサッツに追加します。

## 例

# 単純な調和振動子を定義し、x(t) が周波数 ω で振動することを指定します。

```julia-repl
julia> @variables t, x(t), y(t), ω0, ω, F, k;
julia> diff_eq = DifferentialEquation(d(x,t,2) + ω0^2 * x ~ F * cos(ω*t), x);
julia> add_harmonic!(diff_eq, x, ω) # ω を使用して x を展開

1 つの微分方程式の系
変数:       x(t)
ハーモニックアンサッツ: x(t) => ω;

(ω0^2)*x(t) + Differential(t)(Differential(t)(x(t))) ~ F*cos(t*ω)
```
