```
t8_cmesh_is_partitioned(cmesh)
```

コミットされたcmeshがパーティション化されているか、複製されているかを照会します。

# 引数

  * `cmesh`:[in] コミットされたcmesh。

# 戻り値

*cmesh*がパーティション化されている場合はTrue。そうでない場合はFalse。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
int t8_cmesh_is_partitioned (t8_cmesh_t cmesh);
```
