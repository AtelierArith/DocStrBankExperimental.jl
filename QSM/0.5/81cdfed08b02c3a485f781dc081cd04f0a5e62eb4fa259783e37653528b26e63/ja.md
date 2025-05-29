```
erode_mask(mask::AbstractArray{Bool, 3}, iter::Integer = 1) -> typeof(similar(mask))
```

18ステンシルキューブを使用してバイナリマスクを侵食します。

### 引数

  * `mask::AbstractArray{Bool, 3}`: バイナリマスク
  * `iter::Integer = 1`: `iter`回侵食する

### 戻り値

  * `typeof(similar(mask))`: 侵食されたバイナリマスク
