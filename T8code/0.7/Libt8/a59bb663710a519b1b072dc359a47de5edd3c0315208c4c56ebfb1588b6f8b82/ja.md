```
t8_cmesh_set_tree_class(cmesh, gtree_id, tree_class)
```

cmesh内の木のクラスを設定します。t8*cmesh*commitの後にこの関数を呼び出すことは許可されていません。同じ木に対してこの関数を複数回呼び出すことも許可されていません。

# 引数

  * `cmesh`:[in,out] 更新されるcmesh。
  * `tree_id`:[in] 木のグローバル番号。
  * `tree_class`:[in] この木の要素クラス。

### プロトタイプ

```c
void t8_cmesh_set_tree_class (t8_cmesh_t cmesh, t8_gloidx_t gtree_id, t8_eclass_t tree_class);
```
