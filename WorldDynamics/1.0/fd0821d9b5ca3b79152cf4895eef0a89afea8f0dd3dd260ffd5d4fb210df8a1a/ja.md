`plotvariables(solution, xrange, variables::Vector{<:NTuple{4, Any}}; title="", showaxis=true, showlegend=true, linetype="lines", colored=true)`

ODEシステム`solution`によって得られたベクトル`variables`の値を指定された`xrange`区間でプロットします（通常、`solvesystems.jl`の`solve`関数を使用して得られます）。各変数について、ベクトル`variables`には、Julia変数、その範囲、およびプロットに表示される記号名を含む4つ組が含まれています。
