```
aws_event_stream_write_headers_to_buffer(headers, buffer)
```

このAPIは安全ではないため、'[ `aws_event_stream_write_headers_to_buffer_safe`](@ref)' の使用が推奨されています。

ヘッダーをバッファに書き込み、バッファに書き込まれたバイト数の長さを返します。バッファがヘッダーを格納するのに十分な大きさであると仮定します。

### プロトタイプ

```c
size_t aws_event_stream_write_headers_to_buffer(const struct aws_array_list *headers, uint8_t *buffer);
```
