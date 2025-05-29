`SODEProblem`: 分割常微分方程問題

初期値問題を定義します

$$
\dot{q} (t) = v(t, q(t)) , \qquad q(t_{0}) = q_{0} ,
$$

ベクトル場 $v$、初期条件 $q_{0}$、および解 $q$ は $\mathbb{R}^{d}$ の値を取ります。ここで、ベクトル場 $v$ はベクトル場の和として与えられます

$$
v (t) = v_1 (t) + ... + v_r (t) .
$$

動的変数 $q$ は初期条件 $q_{0}$ を持ち、$\mathbb{R}^{d}$ の値を取ります。

### コンストラクタ

```julia
SODEProblem(v, q, tspan, tstep, ics::NamedTuple; kwargs...)
SODEProblem(v, q, tspan, tstep, q₀::StateVariable; kwargs...)
SODEProblem(v, q, tspan, tstep, q₀::AbstractArray; kwargs...)
SODEProblem(v, tspan, tstep, ics::NamedTuple; kwargs...)
SODEProblem(v, tspan, tstep, q₀::StateVariable; kwargs...)
SODEProblem(v, tspan, tstep, q₀::AbstractArray; kwargs...)
```

ここで `v` は各サブステップのベクトル場を計算する関数のタプル、`q` は各サブステップの解を計算する関数のオプショナルなタプル、`tspan` は問題を解くための時間区間 `(t₀,t₁)`、`tstep` はシミュレーションで使用される時間ステップ、`ics` はエントリ `q` を持つ `NamedTuple` です。初期条件 `q₀` は直接指定することもでき、`StateVariable` は `AbstractArray{<:Number}` です。

可能なキーワード引数については、[`EquationProblem`](@ref GeometricEquations.EquationProblem) サブタイプのドキュメントを参照してください。

### 関数定義

ベクトル場を提供する関数 `v_i` は次のインターフェースを持たなければなりません

```julia
function v_i(v, t, q, params)
    v[1] = ...
    v[2] = ...
    ...
end
```

解を提供する関数 `q_i` は次のインターフェースを持たなければなりません

```julia
function q_i(q₁, t₁, q₀, t₀, params)
    q₁[1] = q₀[1] + ...
    q₁[2] = q₀[2] + ...
    ...
end
```

ここで `t₀` は現在の時間、`q₀` は現在の解ベクトル、`q₁` は時間 `t₁` における新しい解ベクトルであり、1つのサブステップを計算した結果を保持します。

関数 `v` が解を返し、各サブステップのベクトル場だけでなくなることは、分割法の使用に対する柔軟性を高めます。例えば、ベクトル場 $v_i$ を解くために別の積分器を使用することが可能になります。
