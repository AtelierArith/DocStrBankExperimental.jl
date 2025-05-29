```
gaspi_group_create(group)
```

グループを作成します。成功した場合、メンバーなしの空のグループが作成されます。

### パラメータ

  * `group`: 作成されたグループ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_group_create (gaspi_group_t * const group);
```
