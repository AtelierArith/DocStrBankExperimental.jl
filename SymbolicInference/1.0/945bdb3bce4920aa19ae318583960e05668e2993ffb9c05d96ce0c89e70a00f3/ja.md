```
extract_recurrences_joint(data_source::Vector{Float64}, data_source2::Vector{Float64},
    motifs_dict::Dict{String, Vector}; num_windows::Int64 = 3)

    この関数は、2つの時系列から検出された各モチーフの開始位置とサイズを考慮して、与えられたウィンドウのxおよびy座標を返します。
```

y座標は、ユーザーが提供したデータの値です。
