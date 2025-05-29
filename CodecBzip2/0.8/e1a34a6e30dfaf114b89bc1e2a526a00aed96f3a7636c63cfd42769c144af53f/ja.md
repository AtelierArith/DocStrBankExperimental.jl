```
Bzip2Compressor(;blocksize100k=9, workfactor=30, verbosity=0)
```

bzip2圧縮コーデックを作成します。

## 引数

  * `blocksize100k`: 圧縮に使用するブロックサイズ (1..9)
  * `workfactor`: 標準アルゴリズムがフォールバックに頼る前に費やす努力の量 (0..250)
  * `verbosity`: 冗長性レベル (0..4)

!!! warning
    `serialize` と `deepcopy` は、保存された生ポインタのため、このコーデックでは機能しません。

