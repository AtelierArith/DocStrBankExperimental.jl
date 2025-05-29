```
aws_event_stream_write_headers_to_buffer_safe(headers, buf)
```

bufがデータを保持するのに十分な大きさであると仮定して、ヘッダーをbufに書き込みます。この関数は、非安全なバリアント「[`aws_event_stream_write_headers_to_buffer`](@ref)」よりも優先してください。

ヘッダーが成功裏に完全に書き込まれた場合はAWS*OP*SUCCESSを返し、それ以外の場合はAWS*OP*ERRを返します。

### プロトタイプ

```c
int aws_event_stream_write_headers_to_buffer_safe( const struct aws_array_list *headers, struct aws_byte_buf *buf);
```
