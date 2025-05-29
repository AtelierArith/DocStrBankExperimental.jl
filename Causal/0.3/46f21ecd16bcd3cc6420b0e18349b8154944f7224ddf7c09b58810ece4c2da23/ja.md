```julia
mutable struct RLCSystem{T1<:Real, T2<:Real, T3<:Real, RH, RO, IP<:(Union{var"#s2876", var"#s2875"} where {var"#s2876"<:Causal.Inport, var"#s2875"<:Nothing}), OP<:(Union{var"#s2874", var"#s2873"} where {var"#s2874"<:Causal.Outport, var"#s2873"<:Nothing}), T4<:(AbstractVector{<:Real}), T5<:(AbstractVector{<:Real}), T6<:(AbstractVector{<:Bool}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractDAESystem
```

RLCシステムを次の動力学で構築します。

$$
\begin{array}{l}
    \dot{x}_1 = x_3 \\[0.25cm]
    \dot{x}_2 = x_4 \\[0.25cm]
    \dot{x}_3 = -\dfrac{F}{m l} x_1 \\[0.25cm]
    \dot{x}_4 = g \dfrac{F}{l} x_2 \\[0.25cm]
    0 = x_1^2 + x_2^2 - l^2 
\end{array}
$$

ここで、$F$は外力、$l$は長さ、$m$は質量、$g$は重力加速度です。
