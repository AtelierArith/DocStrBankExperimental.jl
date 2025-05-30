```
t8_cmesh_is_committed(cmesh)
```

cmeshがNULLでなく、初期化され、コミットされているかどうかを確認します。さらに、cmeshが可能な限り一貫していることを確認します。

# 引数

  * `cmesh`:[in] このcmeshが調べられます。NULLである可能性があります。

# 戻り値

cmeshがNULLでなく、t8*cmesh*initが呼び出され、t8*cmesh*commitが呼び出された場合はTrue。それ以外の場合はFalse。

### プロトタイプ

```c
int t8_cmesh_is_committed (const t8_cmesh_t cmesh);
```
