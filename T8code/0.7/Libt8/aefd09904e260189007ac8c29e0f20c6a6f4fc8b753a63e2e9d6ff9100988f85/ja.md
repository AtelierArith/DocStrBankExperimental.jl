```
t8_cmesh_is_initialized(cmesh)
```

cmeshがNULLでなく、初期化されておらず、コミットされていないかどうかを確認します。さらに、cmeshが可能な限り一貫していることを主張します。

# 引数

  * `cmesh`:[in] このcmeshが調べられます。NULLである可能性があります。

# 戻り値

cmeshがNULLでなく、t8*cmesh*initが呼び出されているが、t8*cmesh*commitは呼び出されていない場合はTrue。それ以外の場合はFalse。

### プロトタイプ

```c
int t8_cmesh_is_initialized (t8_cmesh_t cmesh);
```
