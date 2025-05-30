```
selective_copy!(@nospecialize(h_in::IDS), @nospecialize(h_out::IDS), path::Vector{<:AbstractString}, time0::Float64)
```

指定された time0 で、ある IDS から別の IDS へパスの内容をコピーします（パスが存在する場合）。

注意：

  * パスは i2p(ulocation) です。
  * time0 が NaN の場合、すべての時間が保持されます。
