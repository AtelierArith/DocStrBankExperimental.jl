```
aws_profile_collection_new_from_merge(allocator, config_profiles, credentials_profiles)
```

設定ファイルベースのプロファイルコレクションと資格情報ファイルベースのプロファイルコレクションをマージして新しいプロファイルコレクションを作成します。

### プロトタイプ

```c
struct aws_profile_collection *aws_profile_collection_new_from_merge( struct aws_allocator *allocator, const struct aws_profile_collection *config_profiles, const struct aws_profile_collection *credentials_profiles);
```
