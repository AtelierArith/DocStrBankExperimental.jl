```
updatehalo!(A, include_periodic_bc=false)
```

各ブロック内のハロ領域を同期します。これにより、各スレッド/ブロックが隣接ブロックのドメインから現在のブロックのハロ領域にコピーするタスクが生成されます。

# 引数

  * `A`: `BlockHaloArray`
  * `include_periodic_bc`: 周期境界にあるハロ領域を更新する
