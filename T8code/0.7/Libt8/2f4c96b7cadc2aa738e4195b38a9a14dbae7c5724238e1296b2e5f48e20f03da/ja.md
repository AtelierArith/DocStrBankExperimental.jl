```
t8_forest_is_initialized(forest)
```

フォレストがNULLでなく、初期化されており、コミットされていないかどうかを確認します。さらに、フォレストが可能な限り一貫していることを確認します。

# 引数

  * `forest`:[in] このフォレストが調べられます。NULLである可能性があります。

# 戻り値

フォレストがNULLでなく、t8*forest*initが呼び出されているが、t8*forest*commitが呼び出されていない場合はTrue。それ以外の場合はFalse。

### プロトタイプ

```c
int t8_forest_is_initialized (t8_forest_t forest);
```
