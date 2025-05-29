```
y = dur(x::Grad)
y = dur(x::Vector{Grad})
y = dur(x::Matrix{Grad})
```

Grad構造体またはGrad配列の持続時間[s]。

# 引数

  * `x`: (`::Grad` または `::Vector{Grad}` または `::Matrix{Grad}`) Grad構造体またはGrad配列

# 戻り値

  * `y`: (`::Float64`, `[s]`) Grad構造体またはGrad配列の持続時間
