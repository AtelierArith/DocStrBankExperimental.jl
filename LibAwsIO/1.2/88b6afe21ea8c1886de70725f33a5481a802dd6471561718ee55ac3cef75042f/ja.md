```
aws_server_bootstrap_new_socket_listener(bootstrap_options)
```

サーバーソケットリスナーをセットアップします。TLSを使用する予定がある場合は、代わりに `aws_server_bootstrap_new_tls_socket_listener` を使用してください。これにより、ソケットオプション `options` を使用して `local_endpoint` にバインドされたソケットリスナーが作成されます。 `incoming_callback` は、受信チャネルが使用可能になったとき、またはエラーが発生したときに呼び出されます。 `shutdown_callback` は、チャネルがシャットダウンしたときに呼び出されます。 `destroy_callback` は、サーバーソケットリスナーが破棄され、すべての関連接続とチャネルのシャットダウンが完了した後に呼び出されます。 `shutdown_callback` が返された直後に、チャネルは自動的にクリーンアップされます。すべてのコールバックは、リスニングソケットが割り当てられたイベントループのスレッドで呼び出されます。

`setup_callback`。設定されている場合、リスナーが使用可能になったときにコールバックが非同期的に呼び出されます。Apple Network Frameworkの場合、コールバックが呼び出されるまでリスナーは使用できません。リスナーの作成に失敗した場合（NULLを返す）、`setup_callback` は呼び出されません。

アプリケーションのシャットダウン時には、この関数からの戻り値を使用して [`aws_server_bootstrap_destroy_socket_listener`](@ref) を呼び出す必要があります。

bootstrap_options はコピーされます。

### プロトタイプ

```c
struct aws_socket *aws_server_bootstrap_new_socket_listener( const struct aws_server_socket_channel_bootstrap_options *bootstrap_options);
```
