`PODEProblem`: 分割常微分方程問題

分割常微分方程は、次の形式の初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

ベクトル場 $v$ と $f$ を持っています。

動的変数 $(q,p)$ は初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持ち、値は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ に取ります。

### コンストラクタ

```julia
PODEProblem(v, f, tspan, tstep, ics; kwargs...)
PODEProblem(v, f, tspan, tstep, q₀::StateVariable, p₀::StateVariable; kwargs...)
PODEProblem(v, f, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray; kwargs...)
```

ここで `v` と `f` はベクトル場を計算する関数であり、`tspan` は問題を解くための時間区間 `(t₀,t₁)` で、`tstep` はシミュレーションで使用される時間ステップ、`ics` は `NamedTuple` でエントリ `q` と `p` を持ちます。初期条件 `q₀` と `p₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。関数 `v` と `f` のインターフェースについては [`PODE`](@ref) を参照してください。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに関するドキュメントを参照してください。

### 関数定義

関数 `v` と `f` は次のインターフェースを持たなければなりません。

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end
```

ここで `t` は現在の時間、`q` と `p` は現在の解ベクトル、`v` と `f` は `t`、`q`、`p` に対してベクトル場 $v$ と $f$ を評価した結果を保持するベクトルであり、params は追加のパラメータの `NamedTuple` です。
