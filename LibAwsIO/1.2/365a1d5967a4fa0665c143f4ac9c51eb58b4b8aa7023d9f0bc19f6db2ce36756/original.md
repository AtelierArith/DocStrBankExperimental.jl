```
aws_tls_is_cipher_pref_supported(cipher_pref)
```

Returns true if this Cipher Preference is available in the underlying TLS implementation. This function should always be called before setting a Cipher Preference

### Prototype

```c
bool aws_tls_is_cipher_pref_supported(enum aws_tls_cipher_pref cipher_pref);
```
