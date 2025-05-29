```
aws_host_address_move(from, to)
```

Moves `from` to `to`. After this call, from is no longer usable. Though, it could be resused for another move or copy operation.

### Prototype

```c
void aws_host_address_move(struct aws_host_address *from, struct aws_host_address *to);
```
