```
p8est_connectivity_sink(conn, sink)
```

接続性をシンクオブジェクトに書き込みます。

### パラメータ

  * `conn`:[in] 書き込む接続性。
  * `sink`:[in,out] このシンクに接続性が書き込まれます。

### 戻り値

成功時は0、エラー時は非ゼロ。

### プロトタイプ

```c
int p8est_connectivity_sink (p8est_connectivity_t * conn, sc_io_sink_t * sink);
```
