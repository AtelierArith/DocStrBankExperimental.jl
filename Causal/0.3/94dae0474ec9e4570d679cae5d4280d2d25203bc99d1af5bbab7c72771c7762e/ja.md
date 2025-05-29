```julia
mutable struct Integrator{T1<:Real, RH, RO, ST<:(AbstractVector{<:Real}), IP<:(Union{var"#s2879", var"#s2878"} where {var"#s2879"<:Causal.Inport, var"#s2878"<:Nothing}), OP<:(Union{var"#s2877", var"#s2876"} where {var"#s2877"<:Causal.Outport, var"#s2876"<:Nothing}), var"356", var"357", var"358", Symbol, var"359", Float64, var"360", var"361", var"362", var"363", var"364", var"365"} <: Causal.AbstractODESystem
```

入力出力関係が次のように与えられる積分器を構築します。

$$
u(t) = ki * \int_{0}^{t} u(\tau) d\tau
$$

ここで、$u(t)$は入力、$y(t)$は出力、$ki$は積分定数です。
