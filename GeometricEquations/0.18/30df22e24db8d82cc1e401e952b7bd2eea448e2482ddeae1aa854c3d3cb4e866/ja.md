`SDEProblem`: ストラトノビッチ確率微分方程式問題

確率微分初期値問題を定義します

$$
\begin{aligned}
dq (t) &= v(t, q(t)) \, dt + B(t, q(t)) \circ dW , & q(t_{0}) &= q_{0} ,
\end{aligned}
$$

ドリフトベクトル場 $v$、拡散行列 $B$、初期条件 $q_{0}$、動的変数 $q$ は $\mathbb{R}^{d}$ の値を取り、m次元ウィーナー過程 W があります。

### コンストラクタ

```julia
SDEProblem(v, B, tspan, tstep, ics::NamedTuple; kwargs...)
SDEProblem(v, B, tspan, tstep, q₀::StateVariable; kwargs...)
```

ここで `v` はベクトル場を計算する関数であり、`B` は拡散行列を計算します。`tspan` は問題を解くための時間区間 `(t₀,t₁)` であり、`tstep` はシミュレーションで使用される時間ステップです。`ics` はエントリ `q` を持つ `NamedTuple` です。初期条件 `q₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) サブタイプのドキュメントを参照してください。

### 関数定義

ドリフトベクトル場と拡散行列を提供する関数 `v` と `B`。関数 `v` は次のインターフェースを持たなければなりません。

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は `t` と `q` に対してベクトル場 $v$ を評価した結果を保持するベクトルであり、params は追加のパラメータです。関数 `B` は次のインターフェースを持つメソッドを持つべきです。

```julia
function B(B, t, q, params)
    B[1,1] = ...
    ...
end
```
