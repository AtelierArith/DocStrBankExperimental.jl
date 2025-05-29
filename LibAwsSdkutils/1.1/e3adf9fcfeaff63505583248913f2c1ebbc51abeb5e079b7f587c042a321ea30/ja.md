```
aws_profile_collection_get_section_count(profile_collection, section_type)
```

指定されたセクションのコレクション内の要素数を返します。

### プロトタイプ

```c
size_t aws_profile_collection_get_section_count( const struct aws_profile_collection *profile_collection, const enum aws_profile_section_type section_type);
```
