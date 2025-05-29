`PSDEProblem`: ストラトノビッチ分割確率微分方程式問題

分割確率微分方程式は、次の形の初期値問題です。

$$
\begin{aligned}
dq (t) &= v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= f(t, q(t), p(t)) \, dt + G(t, q(t), p(t)) \circ dW , & p(t_{0}) &= p_{0}
\end{aligned}
$$

ここで、ドリフトベクトル場 $v$ と $f$、拡散行列 $B$ と $G$、初期条件 $q_{0}$ と $p_{0}$、動的変数 $(q,p)$ は $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取り、m次元ウィーナー過程 W があります。

### コンストラクタ

```julia
PSDEProblem(v, f, B, G, tspan, tstep, ics::NamedTuple; kwargs...)
PSDEProblem(v, f, B, G, tspan, tstep, q₀::StateVariable; p₀::StateVariable; kwargs...)
```

ここで `v` と `f` はベクトル場を計算する関数であり、`B` と `G` は拡散行列を計算します。`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。`ics` はエントリ `q` を持つ `NamedTuple` です。初期条件 `q₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) サブタイプのドキュメントを参照してください。

### 関数定義

関数 `v`、`f`、`B` および `G` は、ドリフトベクトル場と拡散行列を提供し、それぞれ5つの引数を取ります。`v(v, t, q, p, params)`、`f(f, t, q, p, params)`、`B(B, t, q, p, params)` および `G(G, t, q, p, params)` であり、ここで `t` は現在の時間、`(q, p)` は現在の解、`v`、`f`、`B` および `G` は `t` と `(q,p)` に対してベクトル場 $v$、$f$ および行列 $B$、$G$ を評価した結果を保持する変数であり、`params` はオプションのパラメータです。

対応するメソッドは次のシグネチャを持つべきです。

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

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```
