```
aws_websocket_increment_read_window(websocket, size)
```

フレームの流れを維持するために、読み取りウィンドウを手動で増加させます。

`manual_window_management`がtrueに設定されている場合、読み取りウィンドウが0に達するとデータの受信が停止します。ウェブソケットの`initial_window_size`は、読み取りウィンドウの開始サイズを決定します。読み取りウィンドウは、「データ」フレーム（TEXT、BINARY、CONTINUATION）からペイロードを受信するにつれて縮小します。ウィンドウを再度増加させてフレームの流れを維持するには、[`aws_websocket_increment_read_window`](@ref)()を使用します。高いスループットを維持するために、より大きなウィンドウを維持してください。「データ」フレームからのペイロードについてのみ心配する必要があります。ウェブソケットは、他のフレームの一部（オペコード、ペイロード長など）や他のフレームタイプ（PING、PONG、CLOSE）のペイロードを含む、他の受信バイトを考慮して自動的にウィンドウを増加させます。

`manual_window_management`がfalseに設定されている場合、この関数は何もしません。

この関数は、任意のスレッドから呼び出すことができます。

### プロトタイプ

```c
void aws_websocket_increment_read_window(struct aws_websocket *websocket, size_t size);
```
