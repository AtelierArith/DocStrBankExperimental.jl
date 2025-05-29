```
erode_mask!(
    emask::AbstractArray{Bool, 3},
    mask::AbstractArray{Bool, 3},
    iter::Integer = 1
) -> emask
```

18ステンシルキューブを使用してバイナリマスクを侵食します。

### 引数

  * `emask::AbstractArray{Bool, 3}`: 侵食されたバイナリマスク
  * `mask::AbstractArray{Bool, 3}`: バイナリマスク
  * `iter::Integer = 1`: `iter`回侵食する

### 戻り値

  * `emask`: 侵食されたバイナリマスク
