```
gaspi_proc_ping(rank, tout)
```

特定のプロセス（ランク）に対してピンを送信します。これは、ランクが生存しているかどうかを判断するためにFTアプリケーションで役立ちます。

### パラメータ

  * `rank`: ピンを送信するランク。
  * `tout`: ミリ秒単位のタイムアウト値。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_ping (const gaspi_rank_t rank, gaspi_timeout_t tout);
```
