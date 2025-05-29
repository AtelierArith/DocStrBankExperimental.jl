```
gaspi_proc_rank(rank)
```

プロセスのランクを取得します。

### パラメータ

  * `rank`: 呼び出しプロセスのランク。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_rank (gaspi_rank_t * const rank);
```
