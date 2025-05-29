```
lop3(a, b, c, lut)
```

任意の論理演算を3つの入力に対して行います。

[PTX `prmt` 命令](https://docs.nvidia.com/cuda/parallel-thread-execution/index.html#data-movement-and-conversion-instructions-prmt)を呼び出します。これは、入力 `a`、`b`、および `c` に対してビット単位の論理演算を計算します。

`lut` のルックアップテーブルを作成するには [`make_lop3_lut`](@ref) を参照してください。
