```
aws_socket_validate_port_for_connect(port, domain)
```

このポートへの接続が不正な場合、AWS*IO*SOCKET*INVALID*ADDRESSを発生させ、エラーをログに記録します。たとえば、ポートはIPv4で接続するために1-65535の範囲内でなければなりません。これらのポート値は最終的に[`aws_socket_connect`](@ref)()で失敗しますが、この関数を使用して早期に検証することができます。

### プロトタイプ

```c
int aws_socket_validate_port_for_connect(uint32_t port, enum aws_socket_domain domain);
```
