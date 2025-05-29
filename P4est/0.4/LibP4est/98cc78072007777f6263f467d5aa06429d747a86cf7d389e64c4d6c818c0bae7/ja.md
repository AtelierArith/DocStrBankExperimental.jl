```
p4est_connectivity_set_attr(conn, bytes_per_tree)
```

接続における属性フィールドを割り当てるか解放します。

### パラメータ

  * `conn`:[in,out] conn->**to*attr フィールドは NULL であるか、この関数によって以前に割り当てられている必要があります。
  * `bytes_per_tree`:[in] 0 の場合、tree*to*attr は解放されます（NULL であることは問題ありません）。正の値の場合、要求されたスペースが割り当てられます。

### プロトタイプ

```c
void p4est_connectivity_set_attr (p4est_connectivity_t * conn, size_t bytes_per_tree);
```
