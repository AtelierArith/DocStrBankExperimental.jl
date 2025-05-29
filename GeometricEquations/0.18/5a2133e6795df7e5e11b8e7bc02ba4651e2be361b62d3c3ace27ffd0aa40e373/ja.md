`HODEProblem`: ハミルトン常微分方程式問題

標準的なハミルトン系の方程式は、分割された常微分方程式の特別なケースです。

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

ベクトル場 $v$ と $f$ は次のように与えられます。

$$
\begin{aligned}
v &=   \frac{\partial H}{\partial p} , &
f &= - \frac{\partial H}{\partial q} .
\end{aligned}
$$

動的変数 $(q,p)$ は初期条件 $(q(t_{0}) = q_{0}, p(t_{0}) = p_{0})$ を持ち、$T^{*} Q \simeq \mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
HODEProblem(v, f, hamiltonian, tspan, tstep, ics; kwargs...)
HODEProblem(v, f, hamiltonian, tspan, tstep, q₀::StateVariable, p₀::StateVariable; kwargs...)
HODEProblem(v, f, hamiltonian, tspan, tstep, q₀::AbstractArray, p₀::AbstractArray; kwargs...)
```

ここで `v` と `f` はベクトル場を計算する関数であり、`hamiltonian` はハミルトニアンの値（すなわち、全エネルギー）を返します。`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。`ics` は `NamedTuple` で、`q` と `p` のエントリを持ちます。初期条件 `q₀` と `p₀` は、`StateVariable` である `AbstractArray{<:Number}` を用いて直接指定することもできます。関数 `v`、`f`、および `hamiltonian` のインターフェースについては、[`HODE`](@ref) を参照してください。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) のサブタイプに関するドキュメントを参照してください。

### 関数定義

関数 `v`、`f`、および `hamiltonian` は次のインターフェースを持たなければなりません。

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

function hamiltonian(t, q, p, params)
    return ...
end
```

ここで `t` は現在の時間、`q` と `p` は現在の解ベクトル、`v` と `f` は `t`、`q`、および `p` に対してベクトル場を評価した結果を保持するベクトルであり、`params` は追加のパラメータの `NamedTuple` です。
