```
selective_copy!(@nospecialize(h_in::IDS), @nospecialize(h_out::IDS), path::Vector{<:AbstractString}, time0::Float64)
```

指定されたtime0で、あるIDSから別のIDSにパスの内容をコピーします（パスが存在する場合）。

注意：

  * パスはi2p(ulocation)です。
  * time0がNaNの場合、すべての時間が保持されます。
