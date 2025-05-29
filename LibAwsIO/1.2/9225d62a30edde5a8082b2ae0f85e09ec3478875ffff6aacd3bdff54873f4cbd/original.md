```
aws_tls_is_alpn_available()
```

Returns true if alpn is available in the underlying tls implementation. This function should always be called before setting an alpn list.

### Prototype

```c
bool aws_tls_is_alpn_available(void);
```
