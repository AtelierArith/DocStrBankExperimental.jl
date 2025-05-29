```
t8_cmesh_get_first_tree(cmesh)
```

cmesh内の最初のローカルツリーへのポインタを返します。

# 引数

  * `cmesh`:[in] クエリされるcmesh。

# 戻り値

*cmesh*内の最初のローカルツリーへのポインタ。*cmesh*にローカルツリーがない場合は、NULLが返されます。*cmesh*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_ctree_t t8_cmesh_get_first_tree (t8_cmesh_t cmesh);
```
