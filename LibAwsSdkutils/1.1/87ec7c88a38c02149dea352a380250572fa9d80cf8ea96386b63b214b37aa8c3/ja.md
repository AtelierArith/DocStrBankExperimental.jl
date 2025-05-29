```
aws_get_profile_name(allocator, override_name)
```

資格情報の検索に使用するプロファイルを、プロファイル解決ルールに基づいて計算します。

### プロトタイプ

```c
struct aws_string *aws_get_profile_name(struct aws_allocator *allocator, const struct aws_byte_cursor *override_name);
```
