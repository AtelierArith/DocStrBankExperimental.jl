factorize(As::Vector{Array{Float64,2}}, I::Vector{Int})

ブロック対角（遅延）配列の因子を作成します。行列の配列 `As` の各行列に対して `factorize` を呼び出し、インデックス `I` と共にそれらを保存します。
