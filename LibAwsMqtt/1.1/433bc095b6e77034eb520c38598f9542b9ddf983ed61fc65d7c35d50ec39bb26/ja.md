```
aws_mqtt5_listener_new(allocator, config)
```

新しいMQTT5リスナーオブジェクトを作成します。リスナーが生存している限り、受信したパブリッシュとライフサイクルイベントは、リスナーに設定されたコールバックに転送されます。

# 引数

  * `allocator`: 使用するアロケータ
  * `config`: リスナーの設定

# 戻り値

新しい[`aws_mqtt5_listener`](@ref)オブジェクト

### プロトタイプ

```c
struct aws_mqtt5_listener *aws_mqtt5_listener_new( struct aws_allocator *allocator, struct aws_mqtt5_listener_config *config);
```
