```
aws_socket_endpoint_init_local_address_for_test(endpoint)
```

AWS*SOCKET*LOCAL（Unixドメインソケット）で使用するためにランダムなアドレス（UUID）を割り当てます。内部テスト専用です。

### プロトタイプ

```c
void aws_socket_endpoint_init_local_address_for_test(struct aws_socket_endpoint *endpoint);
```
