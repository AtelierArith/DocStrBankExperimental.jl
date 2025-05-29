```
struct LAWorkspace{T}
    I::Vector{UInt32}       # 列のために割り当てられた行インデックス、cost[I[j], j]
    J::Vector{UInt32}       # 行のために割り当てられた列インデックス、cost[i, J[i]]
    u::Vector{T}            # 双対行変数
    v::Vector{T}            # 双対列変数
    d::Vector{T}            # 最短経路の長さ
    p::Vector{UInt32}       # 最短経路木の前駆体配列
    sr::Vector{Bool}        # スキャンされた行
    sc::Vector{Bool}        # スキャンされた列
    free::Vector{UInt32}    # 割り当てられていない行
    feasible::Ref{Bool}     # 実行可能な割り当て
end

LAWorkspace(cost::AbstractMatrix{T}) -> LAWorkspace{T}
LAWorkspace(::Type{T}, cost::AbstractMatrix) -> LAWorkspace{T}
LAWorkspace(::Type{T}, m::Integer, n::Integer) -> LAWorkspace{T}
```
