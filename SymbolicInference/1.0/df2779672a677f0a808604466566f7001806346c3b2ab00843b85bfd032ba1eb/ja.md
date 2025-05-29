extract*recurrences(data*source::Vector{Float64}, motifs*dict::Dict{String, Vector}; num*windows::Int64 = 3)

この関数は、各モチーフの開始位置とサイズを考慮して、与えられたウィンドウのxおよびy座標を返します。y座標は、ユーザーが提供したデータの値です。
