```
aws_crt_statistics_socket_reset(stats)
```

Resets socket channel handler statistics for the next gather interval. Calculate-once results are left alone.

### Prototype

```c
void aws_crt_statistics_socket_reset(struct aws_crt_statistics_socket *stats);
```
