```
aws_channel_slot_downstream_read_window(slot)
```

ダウンストリーム読み取りウィンドウを取得します。これにより、読み取りウィンドウを尊重するために必要な情報が得られます。send_message()を呼び出し、このウィンドウを超えると、メッセージは拒否されます。

### プロトタイプ

```c
size_t aws_channel_slot_downstream_read_window(struct aws_channel_slot *slot);
```
