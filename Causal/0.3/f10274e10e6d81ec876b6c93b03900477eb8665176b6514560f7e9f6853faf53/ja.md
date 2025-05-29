```julia
mutable struct ContinuousLinearSystem{T1<:(AbstractMatrix{<:Real}), T2<:(AbstractMatrix{<:Real}), T3<:(AbstractMatrix{<:Real}), T4<:(AbstractMatrix{<:Real}), IP<:(Union{var"#s1444", var"#s1443"} where {var"#s1444"<:Causal.Inport, var"#s1443"<:Nothing}), OP<:(Union{var"#s778", var"#s777"} where {var"#s778"<:Causal.Outport, var"#s777"<:Nothing}), ST<:(AbstractVector{<:Real}), RH, RO, var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

`input` と `output` を持つ `ContinuousLinearSystem` を構築します。`state` は初期状態で、`t` は時間です。`modelargs` と `modelkwargs` は `ODEProblem` に渡され、`solverargs` と `solverkwargs` は `DifferentialEquations` の `solve` メソッドに渡されます。`alg` はシステムの微分方程式を解くためのアルゴリズムです。

`ContinuousLinearSystem` は以下の状態と出力の方程式で表されます。

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
  * `input::Union{var"#s1444", var"#s1443"} where {var"#s1444"<:Causal.Inport, var"#s1443"<:Nothing}`: 入力。`Inport` または `Nothing` であることが期待されます
  * `output::Union{var"#s778", var"#s777"} where {var"#s778"<:Causal.Outport, var"#s777"<:Nothing}`: 出力ポート
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
