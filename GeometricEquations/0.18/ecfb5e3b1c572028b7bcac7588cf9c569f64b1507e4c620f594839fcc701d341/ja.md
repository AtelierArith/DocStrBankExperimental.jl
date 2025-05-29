`ODEProblem`: 常微分方程問題

常微分方程は、次の形式の初期値問題を定義します。

$$
\dot{q} (t) = v(t, q(t)) ,
$$

ベクトル場 $v$ を持つ。

初期条件 $q_{0}$ を持つ動的変数 $q$ は $\mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
ODEProblem(v, tspan, tstep, ics::NamedTuple; kwargs...)
ODEProblem(v, tspan, tstep, q₀::StateVariable; kwargs...)
ODEProblem(v, tspan, tstep, q₀::AbstractArray; kwargs...)
```

ここで `v` はベクトル場を計算する関数であり、`tspan` は問題を解くための時間区間 `(t₀,t₁)` で、`tstep` はシミュレーションで使用される時間ステップであり、`ics` は `StateVariable` 型のエントリ `q` を持つ `NamedTuple` です。初期条件 `q₀` は、`StateVariable` または `AbstractArray{<:Number}` として直接指定することもできます。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) サブタイプのドキュメントを参照してください。

### 関数定義

ベクトル場を提供する関数 `v` は、次のインターフェースを持たなければなりません。

```julia
function v(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

ここで `t` は現在の時間、`q` は現在の解ベクトル、`v` は `t` と `q` に対してベクトル場 $v$ を評価した結果を保持するベクトルであり、`params` はベクトル場が依存する可能性のある追加のパラメータの `NamedTuple` です。
