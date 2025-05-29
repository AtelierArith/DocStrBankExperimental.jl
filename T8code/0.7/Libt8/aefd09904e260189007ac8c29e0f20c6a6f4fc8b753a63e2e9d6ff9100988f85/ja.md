```
t8_cmesh_is_initialized(cmesh)
```

cmeshがNULLでなく、初期化されており、コミットされていないかどうかを確認します。さらに、cmeshが可能な限り一貫性があることを確認します。

# 引数

  * `cmesh`:[in] このcmeshが調べられます。NULLである可能性があります。

# 戻り値

cmeshがNULLでなく、t8*cmesh*initが呼び出されているが、t8*cmesh*commitは呼び出されていない場合は真。それ以外の場合は偽。

### プロトタイプ

```c
int t8_cmesh_is_initialized (t8_cmesh_t cmesh);
```
