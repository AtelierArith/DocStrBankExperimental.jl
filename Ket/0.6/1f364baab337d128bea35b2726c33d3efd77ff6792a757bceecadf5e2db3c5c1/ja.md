```
pretty_good_measurement(ρ::Vector{<:AbstractMatrix}, q::Vector{<:Real} = ones(length(ρ)))
```

ベクトル状態 `ρ` を確率 `q` で識別するための、かなり良い測定POVMを計算します。`q` が省略された場合は、一様であると見なされます。

参考文献: Watrous, [量子情報の理論 第3章](https://cs.uwaterloo.ca/~watrous/TQI/TQI.3.pdf)
