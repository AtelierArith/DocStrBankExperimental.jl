```julia
mutable struct DiscreteLinearSystem{T1<:(AbstractMatrix{<:Real}), T2<:(AbstractMatrix{<:Real}), T3<:(AbstractMatrix{<:Real}), T4<:(AbstractMatrix{<:Real}), IP<:(Union{var"#s2873", var"#s2872"} where {var"#s2873"<:Causal.Inport, var"#s2872"<:Nothing}), OP<:(Union{var"#s2871", var"#s2870"} where {var"#s2871"<:Causal.Outport, var"#s2870"<:Nothing}), ST<:(AbstractVector{<:Real}), RH, RO, var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDiscreteSystem
```

`input` と `output` を持つ `DiscreteLinearSystem` を構築します。`state` は初期状態で、`t` は時間です。`modelargs` と `modelkwargs` は `ODEProblem` に渡され、`solverargs` と `solverkwargs` は `DifferentialEquations` の `solve` メソッドに渡されます。`alg` はシステムの微分方程式を解くためのアルゴリズムです。

`DiscreteLinearSystem` は以下の状態と出力の方程式で表されます。

$$
\begin{array}{l}
    \dot{x} = A x + B u \\[0.25cm]
    y = C x + D u 
\end{array}
$$

ここで $x$ は `state` です。`solver` は上記の微分方程式を解くために使用されます。

# フィールド

  * `A::AbstractMatrix{<:Real}`: A
  * `B::AbstractMatrix{<:Real}`: B
  * `C::AbstractMatrix{<:Real}`: C
  * `D::AbstractMatrix{<:Real}`: D
  * `input::Union{var"#s2873", var"#s2872"} where {var"#s2873"<:Causal.Inport, var"#s2872"<:Nothing}`: 入力。`Inport` または `Nothing` であることが期待されます
  * `output::Union{var"#s2871", var"#s2870"} where {var"#s2871"<:Causal.Outport, var"#s2870"<:Nothing}`: 出力ポート
  * `state::AbstractVector{<:Real}`: 状態
  * `righthandside::Any`: 右辺関数
  * `readout::Any`: 読み出し関数
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
