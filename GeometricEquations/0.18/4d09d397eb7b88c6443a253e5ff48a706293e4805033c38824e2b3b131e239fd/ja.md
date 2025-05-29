`PODEEnsemble`: 分割常微分方程アンサンブル

分割常微分方程は、次の形式の初期値問題です。

$$
\begin{aligned}
\dot{q} (t) &= v(t, q(t), p(t)) , \\
\dot{p} (t) &= f(t, q(t), p(t)) ,
\end{aligned}
$$

ベクトル場 $v$ と $f$ を持っています。

動的変数 $(q,p)$ は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
PODEEnsemble(v, f, tspan, tstep, ics::AbstractVector{<: NamedTuple}; kwargs...)
PODEEnsemble(v, f, tspan, tstep, q₀::AbstractVector{<: StateVariable}, p₀::AbstractVector{<: StateVariable}; kwargs...)
PODEEnsemble(v, f, tspan, tstep, q₀::AbstractVector{<: AbstractArray}, p₀::AbstractVector{<: AbstractArray}; kwargs...)
```

ここで `v` と `f` はベクトル場を計算する関数であり、`tspan` は問題を解くための時間区間 `(t₀,t₁)` で、`tstep` はシミュレーションで使用される時間ステップ、`ics` は `NamedTuple` のエントリ `q` と `p` を持つ `AbstractVector` です。初期条件 `q₀` と `p₀` も指定でき、それぞれ `StateVariable` または `AbstractArray{<:Number}` の `AbstractVector` として指定できます。関数 `v` と `f` のインターフェースについては [`PODE`](@ref) を参照してください。

可能なキーワード引数については、[`EnsembleProblem`](@ref GeometricEquations.EnsembleProblem) サブタイプのドキュメントを参照してください。
