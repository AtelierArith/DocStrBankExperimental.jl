```
active_blocks(fun::CuFunction, threads; shmem=0)
```

カーネル `fun` を実行する `threads` スレッドのとき、動的共有メモリが `shmem` バイト必要な場合、マルチプロセッサあたりのアクティブブロックの最大数を計算します。
