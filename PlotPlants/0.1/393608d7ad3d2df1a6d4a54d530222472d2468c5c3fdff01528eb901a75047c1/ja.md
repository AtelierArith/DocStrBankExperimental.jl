```
set_xticks!(axs::Array, xticks::Array)
set_xticks!(axs::Array,
            xticks::Union{Array{Int,1},Array{Float32,1},Array{Float64,1}}
)
```

与えられたX軸の目盛りを設定します

  * `axs` 軸の配列
  * `xticks` X軸の目盛りの配列
