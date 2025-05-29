```
gaspi_group_add(group, rank)
```

指定されたランクをグループに追加します。

### パラメータ

  * `group`: 追加するグループ。
  * `rank`: グループに追加するランク。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_group_add (const gaspi_group_t group, const gaspi_rank_t rank);
```
