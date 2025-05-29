```
aws_is_network_interface_name_valid(interface_name)
```

ネットワークインターフェイス名が有効かどうかを検証します。Windowsでは、network*interface*nameをサポートしていないため、常にfalseを返します。

### プロトタイプ

```c
bool aws_is_network_interface_name_valid(const char *interface_name);
```
