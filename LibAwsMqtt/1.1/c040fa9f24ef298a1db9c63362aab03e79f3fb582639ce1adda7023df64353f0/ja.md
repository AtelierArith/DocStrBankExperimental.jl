```
aws_mqtt_client_new(allocator, bootstrap)
```

[`aws_mqtt_client`](@ref) のインスタンスを作成します。

# 引数

  * `allocator`:[in] クライアントが今後のすべての割り当てに使用するアロケータ
  * `bootstrap`:[in] 新しいソケット接続を開始するために使用するクライアントブートストラップ

# 戻り値

成功した場合は新しい[`aws_mqtt_client`](@ref)のインスタンス、そうでない場合はNULL

### プロトタイプ

```c
struct aws_mqtt_client *aws_mqtt_client_new(struct aws_allocator *allocator, struct aws_client_bootstrap *bootstrap);
```
