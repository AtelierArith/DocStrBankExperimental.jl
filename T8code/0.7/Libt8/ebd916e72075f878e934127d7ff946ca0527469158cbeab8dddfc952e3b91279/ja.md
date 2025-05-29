```
t8_cmesh_get_num_trees(cmesh)
```

cmesh内の木のグローバル数を返します。

# 引数

  * `cmesh`:[in] 考慮されるcmesh。

# 戻り値

*cmesh*に関連付けられた木の数。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_gloidx_t t8_cmesh_get_num_trees (t8_cmesh_t cmesh);
```
