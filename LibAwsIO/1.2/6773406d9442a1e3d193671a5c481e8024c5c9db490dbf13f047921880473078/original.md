```
aws_tls_connection_options_copy(to, from)
```

Cleans up 'to' and copies 'from' to 'to'. 'to' must be initialized.

### Prototype

```c
int aws_tls_connection_options_copy( struct aws_tls_connection_options *to, const struct aws_tls_connection_options *from);
```
