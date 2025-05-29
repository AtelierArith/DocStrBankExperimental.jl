```
openblas_setaffinity(mask; threadid)
```

指定された `threadid` を持つ OpenBLAS スレッドのアフィニティを指定された `mask` に設定します。

入力 `mask` は次のいずれかである必要があります：

  * マスクを直接示す `BitArray`
  * cpuids のベクター（この場合、マスクは自動的に構築されます）
