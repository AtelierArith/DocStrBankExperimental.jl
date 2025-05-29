```
gaspi_group_num(group_num)
```

現在作成されているグループの数を取得します。

### パラメータ

  * `group_num`: グループの数を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_group_num (gaspi_number_t * const group_num);
```
