```
gaspi_group_ranks(group, group_ranks)
```

指定されたグループを形成するランクのリストを取得します。

### パラメータ

  * `group`: 我々が関心を持っているグループ。
  * `group_ranks`: 出力パラメータ：指定されたグループに属するランクの配列。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_group_ranks (const gaspi_group_t group, gaspi_rank_t * const group_ranks);
```
