```
aws_server_socket_channel_bootstrap_options
```

サーバーソケットリスナーをセットアップするための引数で、TLSの交渉と設定も行います。これは、ソケットオプション `options` と TLSオプション `tls_options` を使用して、`host` と `port` にバインドされたソケットリスナーを作成します。`incoming_callback` は、受信チャネルが使用可能になり、TLSの交渉が完了したとき、またはエラーが発生したときに呼び出されます。`shutdown_callback` は、チャネルがシャットダウンしたときに呼び出されます。`destroy_callback` は、サーバーソケットリスナーが破棄された後、すべての関連接続とチャネルがシャットダウンを完了した後に呼び出されます。`shutdown_callback` が返された直後に、チャネルは自動的にクリーンアップされます。すべてのコールバックは、リスナーが割り当てられたイベントループのスレッド内で呼び出されます。

アプリケーションのシャットダウン時には、この関数からの戻り値を使用して [`aws_server_bootstrap_destroy_socket_listener`](@ref) を呼び出す必要があります。

`options` のソケットタイプは、`tls_options` が設定されている場合、AWS*SOCKET*STREAM でなければなりません。TLSに対してDTLSは現在サポートされていません。
