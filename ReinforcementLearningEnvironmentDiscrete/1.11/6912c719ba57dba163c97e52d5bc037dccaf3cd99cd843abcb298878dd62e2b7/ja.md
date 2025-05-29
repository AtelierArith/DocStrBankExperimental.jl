```
mutable struct MDP 
    ns::Int64
    na::Int64
    state::Int64
    trans_probs::Array{AbstractArray, 2}
    reward::Array{Float64, 2}
    initialstates::Array{Int64, 1}
    isterminal::Array{Int64, 1}
```

`ns` 状態、`na` 行動、現在の `state`、`na`x`ns` の遷移確率の配列 `trans_props` を持つマルコフ決定過程で、これは各 (行動, 状態) ペアに対して (潜在的にスパースな) 配列が 1 に合計される (遷移確率を構築するためのヘルパーとして [`getprobvecrandom`](@ref)、[`getprobvecuniform`](@ref)、[`getprobvecdeterministic`](@ref) を参照) `na`x`ns` の報酬の配列 `reward`、初期状態の配列 `initialstates`、および状態が終端であるかどうかを示す 0/1 の配列 `ns` を持っています。
