```
hardcall!(c::AbstractArray{I}, d::AbstractArray{T}; threshold=0.1) where {I, T}
```

ハード遺伝子型コールをドージャスに対して行います。`d`はドージャスベクトルで、`c`は値が0、1、2、または9（欠損値）のハードコールされた遺伝子型で満たされます。`threshold`はハードコールとドージャスの最大距離を決定します。`threshold`は[0, 0.5)の範囲内でなければなりません。
