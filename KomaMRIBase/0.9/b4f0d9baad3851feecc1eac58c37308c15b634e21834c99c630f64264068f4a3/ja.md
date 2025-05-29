```
y = dur(x::RF)
y = dur(x::Vector{RF})
y = dur(x::Matrix{RF})
```

RF構造体またはRF配列の持続時間 [s]。

# 引数

  * `x`: （`::RF` または `::Vector{RF}` または `::Matrix{RF}`）RF構造体またはRF配列

# 戻り値

  * `y`: （`::Float64`, [`s`]) RF構造体またはRF配列の持続時間
