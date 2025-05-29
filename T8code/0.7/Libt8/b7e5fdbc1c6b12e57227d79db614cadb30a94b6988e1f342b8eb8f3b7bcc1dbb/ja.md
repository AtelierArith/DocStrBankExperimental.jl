```
t8_cmesh_is_empty(cmesh)
```

すべてのプロセスでcmeshが空であるかどうかを確認します。

# 引数

  * `cmesh`:[in] コミットされたcmesh。

# 戻り値

cmeshに木が存在する場合にのみ、真（非ゼロ）を返します。

### プロトタイプ

```c
int t8_cmesh_is_empty (t8_cmesh_t cmesh);
```
