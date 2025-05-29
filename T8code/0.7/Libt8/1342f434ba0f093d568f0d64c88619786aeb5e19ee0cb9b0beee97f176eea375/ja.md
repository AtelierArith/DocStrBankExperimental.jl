```
t8_stash_add_class(stash, id, eclass)
```

ツリーのeclassを設定します。

# 引数

  * `stash`:[in,out] 更新されるスタッシュ。
  * `id`:[in] eclassを設定するツリーのグローバルID。
  * `eclass`:[in] ID *id* のツリーのeclass。

### プロトタイプ

```c
void t8_stash_add_class (t8_stash_t stash, t8_gloidx_t id, t8_eclass_t eclass);
```
