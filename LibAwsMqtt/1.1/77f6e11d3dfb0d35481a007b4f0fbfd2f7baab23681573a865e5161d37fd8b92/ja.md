```
aws_mqtt5_client_new(allocator, options)
```

指定された構成を使用して新しいmqtt5クライアントを作成します

# 引数

  * `allocator`: このクライアントの作成および操作に関連するすべてのメモリ操作に使用するアロケータ
  * `options`: mqtt5クライアントの構成

# 戻り値

新しいmqtt5クライアントまたはNULL

### プロトタイプ

```c
struct aws_mqtt5_client *aws_mqtt5_client_new( struct aws_allocator *allocator, const struct aws_mqtt5_client_options *options);
```
