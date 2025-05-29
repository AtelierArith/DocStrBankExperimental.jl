```
gaspi_proc_init(timeout_ms)
```

GPI-2を開始するための初期化手順です。これは、非ローカルな同期時間ベースのブロッキング手順です。

### パラメータ

  * `timeout_ms`: ミリ秒単位のタイムアウト（またはGASPI*BLOCK/GASPI*TEST）。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーが発生した場合はGASPI*ERROR、タイムアウトが発生した場合はGASPI_TIMEOUTを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_proc_init (const gaspi_timeout_t timeout_ms);
```
