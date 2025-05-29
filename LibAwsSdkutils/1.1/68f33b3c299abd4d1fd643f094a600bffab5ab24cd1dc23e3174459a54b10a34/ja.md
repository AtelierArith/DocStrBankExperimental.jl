```
aws_profile_collection_new_from_buffer(allocator, buffer, source)
```

バッファ内のテキストを解析することによって新しいプロファイルコレクションを作成します。主にテスト用です。

### プロトタイプ

```c
struct aws_profile_collection *aws_profile_collection_new_from_buffer( struct aws_allocator *allocator, const struct aws_byte_buf *buffer, enum aws_profile_source_type source);
```
