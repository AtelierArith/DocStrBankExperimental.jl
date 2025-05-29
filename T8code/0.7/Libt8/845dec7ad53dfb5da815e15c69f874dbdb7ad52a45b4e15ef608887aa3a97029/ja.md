```
t8_cmesh_get_next_tree(cmesh, tree)
```

与えられたローカルツリーに対して、cmesh内の次のローカルツリーへのポインタを返します。

# 引数

  * `cmesh`:[in] クエリされるcmesh。
  * `tree`:[in] *cmesh*内のローカルツリー。

# 戻り値

*tree*の後にある*cmesh*内の次のローカルツリーへのポインタ。該当するツリーが存在しない場合、NULLが返されます。* *cmesh*はこの関数を呼び出す前にコミットされている必要があります。TODO: ツリー番号のみを扱う場合、可能であればAPIでctree_tを使用しないでください。

### プロトタイプ

```c
t8_ctree_t t8_cmesh_get_next_tree (t8_cmesh_t cmesh, t8_ctree_t tree);
```
