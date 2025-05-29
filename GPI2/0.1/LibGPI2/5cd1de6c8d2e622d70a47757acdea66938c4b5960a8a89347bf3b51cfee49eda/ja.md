```
gaspi_proc_local_rank(local_rank)
```

プロセスのローカルランクを取得します。

### パラメータ

  * `local_rank`: 呼び出しプロセスのノード内のランク。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_local_rank (gaspi_rank_t * const local_rank);
```
