```
gaspi_time_ticks(ticks)
```

サイクル数（ティック）を取得します。

### パラメータ

  * `ticks`: ティックを持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_time_ticks (gaspi_cycles_t * const ticks);
```
