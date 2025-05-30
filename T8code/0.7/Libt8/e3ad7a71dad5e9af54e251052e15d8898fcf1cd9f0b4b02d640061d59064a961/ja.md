```
t8_forest_is_committed(forest)
```

フォレストがNULLでなく、初期化され、コミットされているかどうかを確認します。さらに、フォレストが可能な限り一貫していることを主張します。

# 引数

  * `forest`:[in] このフォレストが調べられます。NULLである可能性があります。

# 戻り値

フォレストがNULLでなく、t8*forest*initが呼び出され、t8*forest*commitが呼び出された場合はTrue。それ以外の場合はFalse。

### プロトタイプ

```c
int t8_forest_is_committed (t8_forest_t forest);
```
