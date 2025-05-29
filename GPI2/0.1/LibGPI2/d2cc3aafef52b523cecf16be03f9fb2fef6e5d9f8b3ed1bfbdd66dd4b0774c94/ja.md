```
gaspi_group_size(group, group_size)
```

指定されたグループのサイズを取得します。グループ内のプロセス（ランク）の数を返します。

### パラメータ

  * `group`: サイズを知りたいグループ。
  * `group_size`: グループサイズを格納する出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_group_size (const gaspi_group_t group, gaspi_number_t * const group_size);
```
