`SPSDEProblem`: ストラトノビッチ分割確率微分方程式問題

分割された確率微分初期値問題を定義します

$$
\begin{aligned}
dq (t) &=   v(t, q(t), p(t)) \, dt + B(t, q(t), p(t)) \circ dW , & q(t_{0}) &= q_{0} , \\
dp (t) &= [ f_1(t, q(t), p(t)) + f_2(t, q(t), p(t)) ] \, dt + [ G_1(t, q(t), p(t)) + G_2(t, q(t), p(t)) ] \circ dW , & p(t_{0}) &= p_{0} ,
\end{aligned}
$$

ドリフトベクトル場 $v$ と $f_i$、拡散行列 $B$ と $G_i$、初期条件 $q_{0}$ と $p_{0}$、動的変数 $(q,p)$ が $\mathbb{R}^{d} \times \mathbb{R}^{d}$ の値を取り、m次元ウィーナー過程 W があります。

### コンストラクタ

```julia
SPSDEProblem(v, f1, f2, B, G1, G2, tspan, tstep, ics::NamedTuple; kwargs...)
SPSDEProblem(v, f1, f2, B, G1, G2, tspan, tstep, q₀::StateVariable; p₀::StateVariable; kwargs...)
```

ここで `v` と `f` はベクトル場を計算する関数であり、`Bᵢ` と `Gᵢ` は拡散行列を計算します。`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。`ics` はエントリ `q` を持つ `NamedTuple` です。初期条件 `q₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) サブタイプのドキュメントを参照してください。

### 関数定義

関数 `v`、`f1`、`f2`、`B`、`G1` および `G2` は、ドリフトベクトル場と拡散行列を提供し、すべて5つの引数 `(out, t, q, p, params)` を取ります。

```julia
function v(v, t, q, p, params)
    v[1] = ...
    v[2] = ...
    ...
end

function f1(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function f2(f, t, q, p, params)
    f[1] = ...
    f[2] = ...
    ...
end

function B(B, t, q, p, params)
    B[1,1] = ...
    ...
end

function G1(G, t, q, p, params)
    G[1,1] = ...
    ...
end

function G2(G, t, q, p, params)
    G[1,1] = ...
    ...
end
```

ここで `t` は現在の時間、`(q,p)` は現在の解ベクトルであり、`v`、`f`、`B` および `G` は `(t,q,p)` に対してベクトル場 $v$、$f$ および行列 $B_i$、$G_i$ を評価した結果を保持する変数です。
