```
aws_crt_statistics_tls_reset(stats)
```

Resets tls channel handler statistics for the next gather interval. Calculate-once results are left alone.

### Prototype

```c
void aws_crt_statistics_tls_reset(struct aws_crt_statistics_tls *stats);
```
