```
updateblockhalo!(A::BlockHaloArray, block_id::Integer, include_periodic_bc=false)
```

隣接ブロックから現在のブロックのハロ領域にデータをコピーします

# 引数

  * `A`: `BlockHaloArray`
  * `block_id::Integer`: ブロックインデックス
  * `include_periodic_bc`: 周期境界にあるハロ領域を更新する
