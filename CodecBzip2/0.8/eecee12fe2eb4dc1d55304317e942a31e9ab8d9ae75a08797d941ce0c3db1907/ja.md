```
Bzip2Decompressor(;small=false, verbosity=0)
```

bzip2 デコーディングコーデックを作成します。

## 引数

  * `small`: メモリを少なく使用するアルゴリズムを有効にするフラグ
  * `verbosity`: 冗長性レベル (0..4)

!!! warning
    `serialize` と `deepcopy` は、保存された生ポインタのため、このコーデックでは機能しません。

