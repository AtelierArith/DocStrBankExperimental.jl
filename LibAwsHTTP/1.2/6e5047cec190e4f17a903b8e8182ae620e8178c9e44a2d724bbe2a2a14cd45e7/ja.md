```
aws_http2_connection_update_window(http2_connection, increment_size)
```

接続のフロー制御ウィンドウを増加させてデータの流れを維持します（HTTP/2のみ）。

接続が `conn_manual_window_management` を true に設定して作成された場合、接続のフロー制御ウィンドウは、作成されたすべてのストリームに対してボディデータが受信されると縮小します（ヘッダー、パディング、およびその他のメタデータはウィンドウに影響しません）。初期の接続フロー制御ウィンドウは 65,535 です。接続のフロー制御ウィンドウが 0 に達すると、接続上のすべてのストリームはこれ以上のデータを受信しなくなります。

`conn_manual_window_management` が false の場合、この呼び出しは効果がありません。接続はフロー制御ウィンドウを維持し、バックプレッシャーが適用されず、データが可能な限り速く到着します。

接続されていない場合、この呼び出しは効果がありません。

接続が http2 接続でない場合、クラッシュします。最大サイズの制限は 2**31 - 1 です。また、クライアントは WINDOW_UPDATE フレームが有効であることを確認します。

クライアントは、WINDOW*UPDATE フレームが送信される正確なタイミングを制御します。詳細については `conn*window*size*threshold*to*send_update` を確認してください。

# 引数

  * `http2_connection`: HTTP/2 接続。
  * `increment_size`: 接続のフロー制御ウィンドウを増加させるサイズ

### プロトタイプ

```c
void aws_http2_connection_update_window(struct aws_http_connection *http2_connection, uint32_t increment_size);
```
