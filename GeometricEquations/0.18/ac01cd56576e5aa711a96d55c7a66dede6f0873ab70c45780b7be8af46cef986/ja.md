`HODEEnsemble`: ハミルトン常微分方程式アンサンブル

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

動的変数 $(q,p)$ は $T^{*} Q \simeq \mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
HODEEnsemble(v, f, hamiltonian, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
HODEEnsemble(v, f, hamiltonian, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}; kwargs...)
HODEEnsemble(v, f, hamiltonian, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}; kwargs...)
```

ここで `v` と `f` はベクトル場を計算する関数であり、`hamiltonian` はハミルトニアンの値（すなわち、全エネルギー）を返します。`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。`ics` は `NamedTuple` の `AbstractVector` であり、各エントリには `q` と `p` が含まれます。初期条件 `q₀` と `p₀` も指定でき、各々は `StateVariable` または `AbstractArray{<:Number}` の `AbstractVector` として指定できます。関数 `v`、`f` および `hamiltonian` のインターフェースについては、[`HODE`](@ref) を参照してください。

可能なキーワード引数については、[`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) のサブタイプに関するドキュメントを参照してください。
