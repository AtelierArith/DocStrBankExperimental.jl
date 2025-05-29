```
aws_channel_slot_send_message(slot, message, dir)
```

隣接するスロットにメッセージを送信します。これは、dirに基づいてチャネル内で行われます。また、ウィンドウサイズのチェックも行います。

注意: この関数がエラーコードを返す場合、呼び出し元はメッセージをプールに戻す責任があります。この関数がAWS*OP*SUCCESSを返す場合、メッセージの受信者はメッセージの所有権を取得しています。したがって、たとえば、メッセージをプールに戻してからエラーを返さないでください。この場合、エラー条件に遭遇した場合は、適切なエラーコードでチャネルをシャットダウンしてください。

### プロトタイプ

```c
int aws_channel_slot_send_message( struct aws_channel_slot *slot, struct aws_io_message *message, enum aws_channel_direction dir);
```
