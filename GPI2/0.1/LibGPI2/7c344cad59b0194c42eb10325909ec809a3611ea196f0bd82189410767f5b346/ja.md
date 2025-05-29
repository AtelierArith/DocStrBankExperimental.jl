```
gaspi_threads_sync_all(g, timeout_ms)
```

グループ内のすべてのスレッドを同期します（グローバルバリア）。グループ内で[`gaspi_barrier`](@ref)を含みます。

### パラメータ

  * `group`: バリアに関与するグループ。
  * `timeout`: グローバルバリア（[`gaspi_barrier`](@ref)）に適用されるタイムアウト。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_threads_sync_all(const gaspi_group_t g, const gaspi_timeout_t timeout_ms) __attribute__ ((deprecated));
```
