```
occupancy(fun::CuFunction, threads; shmem=0)
```

カーネル `fun` を起動する `threads` スレッドの理論的な占有率を計算します。`shmem` バイトの動的共有メモリを必要とします。
