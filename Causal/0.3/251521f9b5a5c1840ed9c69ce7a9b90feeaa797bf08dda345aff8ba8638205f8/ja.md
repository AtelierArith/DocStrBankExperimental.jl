```julia
mutable struct VanderpolSystem{T1<:Real, T2<:Real, RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Inport, var"#s2877"<:Nothing}), OP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Outport, var"#s2875"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

`VanderpolSystem`を`input`と`output`で構築します。`mu`と`gamma`はシステムパラメータです。`state`は初期状態で、`t`は時間です。`modelargs`と`modelkwargs`は`ODEProblem`に渡され、`solverargs`と`solverkwargs`は`DifferentialEquations`の`solve`メソッドに渡されます。`alg`はシステムの微分方程式を解くためのアルゴリズムです。

`input`が`nothing`の場合、`VanderpolSystem`の状態方程式は次のようになります。

$$
\begin{array}{l}
    \dot{x}_1 = \gamma (x_2) \\[0.25cm]
    \dot{x}_2 = \gamma (\mu (x_1^2 - 1) x_2 - x_1 )
\end{array}
$$

ここで、$x$は`state`です。`solver`は上記の微分方程式を解くために使用されます。`input`が`nothing`でない場合、状態方程式は次のようになります。

$$
\begin{array}{l}
    \dot{x}_1 = \gamma (x_2) + \sum_{j = 1}^3 \theta_{1j} u_j \\[0.25cm]
    \dot{x}_2 = \gamma (\mu (x_1^2 - 1) x_2 - x_1) + \sum_{j = 1}^3 \theta_{2j} u_j 
\end{array}
$$

ここで、$\Theta = [\theta_{ij}]$は`cplmat`であり、$u = [u_{j}]$は`input`の値です。出力関数は次のようになります。

$$
    y = g(x, u, t)
$$

ここで、$t$は時間`t`、$y$は`output`の値、$g$は`outputfunc`です。

# フィールド

  * `μ::Real`: μ
  * `γ::Real`: γ
  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
  * `state::AbstractVector{<:Real}`: 状態
  * `input::Union{var"#s2878", var"#s2877"} where {var"#s2878"<:Causal.Inport, var"#s2877"<:Nothing}`: 入力。`Inport`または`Nothing`であることが期待されます
  * `output::Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Outport, var"#s2875"<:Nothing}`: 出力ポート
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`
  * `t::Any`
  * `modelargs::Any`
  * `modelkwargs::Any`
  * `solverargs::Any`
  * `solverkwargs::Any`
  * `alg::Any`
  * `integrator::Any`
