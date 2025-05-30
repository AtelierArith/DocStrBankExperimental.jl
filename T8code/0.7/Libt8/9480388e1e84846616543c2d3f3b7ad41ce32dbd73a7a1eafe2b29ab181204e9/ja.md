```
t8_forest_get_local_id(forest, gtreeid)
```

与えられたグローバルツリーIDから、このツリーのフォレストローカルIDを計算します。ツリーがローカルツリーである場合、ローカルIDは0からローカルツリーの数の間になります。ツリーがローカルツリーでない場合、負の数が返されます。

# 引数

  * `forest`:[in] フォレスト。
  * `gtreeid`:[in] ツリーのグローバルID。

# 戻り値

ツリーがローカルツリーである場合、*forest*内のツリーのローカルID。そうでない場合は負の数。

# 参照

https://github.com/DLR-AMR/t8code/wiki/Tree-indexing ツリーインデックスに関する詳細については。

### プロトタイプ

```c
t8_locidx_t t8_forest_get_local_id (const t8_forest_t forest, const t8_gloidx_t gtreeid);
```
