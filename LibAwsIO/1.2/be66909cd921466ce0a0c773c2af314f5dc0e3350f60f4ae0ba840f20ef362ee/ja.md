```
aws_retry_token_acquire(token)
```

トークンの参照カウントを増加させます。これは、所有するポインタにトークンを設定するたびに呼び出す必要があります。

### プロトタイプ

```c
void aws_retry_token_acquire(struct aws_retry_token *token);
```
