```
t8_cmesh_get_first_treeid(cmesh)
```

cmeshの最初のローカルツリーのグローバルインデックスを返します。cmeshがパーティションされていない場合、これは常に0です。

# 引数

  * `cmesh`:[in] 考慮されるcmesh。

# 戻り値

cmesh内の最初のローカルツリーのグローバルID。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_gloidx_t t8_cmesh_get_first_treeid (t8_cmesh_t cmesh);
```
