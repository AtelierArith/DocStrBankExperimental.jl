```
p8est_connectivity_deflate(conn, code)
```

メモリを割り当て、接続情報をそこに保存します。

### パラメータ

  * `conn`:[in] メモリにエクスポートされる接続構造体。
  * `code`:[in] シリアル化のためのエンコーディングおよび圧縮方法。

### 戻り値

情報を含む新しく作成された配列。

### プロトタイプ

```c
sc_array_t *p8est_connectivity_deflate (p8est_connectivity_t * conn, p8est_connectivity_encode_t code);
```
