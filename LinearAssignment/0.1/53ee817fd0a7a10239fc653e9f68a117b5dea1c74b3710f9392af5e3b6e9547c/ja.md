```
struct LAWorkspaceCSC{Tv}
    I::Vector{UInt32}           # 列のために割り当てられた行インデックス、cost[I[j], j]
    J::Vector{UInt32}           # 行のために割り当てられた列インデックス、cost[i, J[i]]
    u::Vector{Tv}               # 双対行変数
    v::Vector{Tv}               # 双対列変数
    d::Vector{Tv}               # 最短経路の長さ
    p::Vector{UInt32}           # 最短経路木の前駆体配列
    srv::Vector{Bool}           # スキャンされた行の訪問状況
    sri::Vector{UInt32}         # スキャンされた行のインデックス
    scv::Vector{Bool}           # スキャンされた列の訪問状況
    sci::Vector{UInt32}         # スキャンされた列のインデックス
    sdv::Vector{Bool}           # 設定された経路の長さの訪問状況
    sdi::Vector{UInt32}         # 設定された経路の長さのインデックス
    qdi::Vector{UInt32}         # スキャンされていない設定された経路の長さのインデックス
    qdj::Vector{UInt32}         # スキャンされていない設定された経路の長さのインデックスの逆
    feasible::RefValue{Bool}    # 実行可能な割り当て
end

LAWorkspaceCSC(cost::SparseMatrixCSC{Tv}) -> LAWorkspaceCSC{Tv}
LAWorkspaceCSC(::Type{Tv}, cost::SparseMatrixCSC) -> LAWorkspaceCSC{Tv}
LAWorkspaceCSC(::Type{Tv}, m::Integer, n::Integer) -> LAWorkspaceCSC{Tv}
```
