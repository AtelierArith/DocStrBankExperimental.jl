```
aws_mqtt5_client_inbound_topic_alias_behavior_type
```

受信トピックエイリアスの動作は、このタイプによって制御されます。

トピックエイリアスの動作については、https://docs.oasis-open.org/mqtt/mqtt/v5.0/os/mqtt-v5.0-os.html#_Toc3901113 に記載されています。

この設定は、クライアントがCONNECTパケットでサーバーにポジティブなトピックエイリアスの最大値を送信するかどうかを制御します。

サーバーがトピックエイリアスをサポートしていない場合、この設定は実質的な効果を持ちません。
