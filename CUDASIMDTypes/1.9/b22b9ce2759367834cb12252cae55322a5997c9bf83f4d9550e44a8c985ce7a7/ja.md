```
prmt(a, b, op)
```

入力ペアからバイトを並べ替えます。

[PTX `prmt` 命令](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#data-movement-and-conversion-instructions-prmt)を呼び出します。これは、入力値 `a` と `b` から任意の4バイトを選択します。
