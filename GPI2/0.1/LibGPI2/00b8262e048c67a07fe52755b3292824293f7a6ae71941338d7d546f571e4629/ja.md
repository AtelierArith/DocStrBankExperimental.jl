```
gaspi_connect(rank, timeout_ms)
```

特定のランクに接続して通信できるようにします。通信に必要なインフラを構築します。

### パラメータ

  * `rank`: 接続するランク。
  * `timeout_ms`: ミリ秒単位のタイムアウト（または GASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合は GASPI*SUCCESS、エラーが発生した場合は GASPI*ERROR、タイムアウトが発生した場合は GASPI_TIMEOUT。

### プロトタイプ

```c
gaspi_return_t gaspi_connect (const gaspi_rank_t rank, const gaspi_timeout_t timeout_ms);
```
