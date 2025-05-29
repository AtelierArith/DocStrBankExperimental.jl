```
gaspi_group_delete(group)
```

指定されたグループを削除します。

### パラメータ

  * `group`: 削除するグループ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_group_delete (const gaspi_group_t group);
```
