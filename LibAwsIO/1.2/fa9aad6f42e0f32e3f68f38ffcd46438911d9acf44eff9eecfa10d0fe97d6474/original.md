```
aws_is_network_interface_name_valid(interface_name)
```

Validates whether the network interface name is valid. On Windows, it will always return false since we don't support network_interface_name on Windows

### Prototype

```c
bool aws_is_network_interface_name_valid(const char *interface_name);
```
