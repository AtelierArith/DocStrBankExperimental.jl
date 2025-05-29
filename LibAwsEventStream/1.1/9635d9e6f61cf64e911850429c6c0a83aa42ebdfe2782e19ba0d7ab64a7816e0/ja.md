```
aws_event_stream_header_value_as_timestamp(header)
```

ヘッダー値を、Unixエポックからのミリ秒を表す64ビット整数として返します。

### プロトタイプ

```c
int64_t aws_event_stream_header_value_as_timestamp(struct aws_event_stream_header_value_pair *header);
```
