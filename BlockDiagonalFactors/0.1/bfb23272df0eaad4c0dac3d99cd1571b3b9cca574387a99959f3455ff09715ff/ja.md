lu(As::Vector{SparseMatrixCSC{Float64,Int}}, I::Vector{Int})

ブロック対角（遅延）因子の配列を作成します。行列の配列 `As` の各行列に対して `lu` を呼び出し、それらをインデックス `I` と共に保存します。
