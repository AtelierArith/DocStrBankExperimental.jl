```
aws_retry_token_record_success(token)
```

Records a successful retry. This is used for making future decisions to open up token buckets, AIMD breakers etc... some strategies such as exponential backoff will ignore this, but you should always call it after a successful operation or your system will never recover during an outage.

### Prototype

```c
int aws_retry_token_record_success(struct aws_retry_token *token);
```
