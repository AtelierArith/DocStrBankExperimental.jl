```
aws_retry_token_acquire(token)
```

Increments reference count for token. This should be called any time you seat the token to a pointer you own.

### Prototype

```c
void aws_retry_token_acquire(struct aws_retry_token *token);
```
