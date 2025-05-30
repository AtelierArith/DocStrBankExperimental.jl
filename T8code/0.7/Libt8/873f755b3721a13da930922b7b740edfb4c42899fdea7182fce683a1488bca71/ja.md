```
t8_offset_in_range(tree_id, proc, offset)
```

与えられたグローバルツリーIDが特定のパーティション内の指定されたプロセスのローカルツリーであるかどうかを判断します。

# 引数

  * `tree_id`:[in] グローバルツリーID。
  * `proc`:[in] MPIランク。
  * `offset`:[in] パーティションテーブル。

# 戻り値

*tree_id* が *offset* 内の *proc* のローカルツリーである場合は非ゼロ、そうでない場合は0を返します。

### プロトタイプ

```c
int t8_offset_in_range (const t8_gloidx_t tree_id, const int proc, const t8_gloidx_t *offset);
```
