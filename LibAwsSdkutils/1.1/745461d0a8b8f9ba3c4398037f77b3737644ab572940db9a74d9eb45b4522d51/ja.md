```
aws_profile_collection_get_profile(profile_collection, profile_name)
```

指定された名前のプロファイルが存在する場合、プロファイルコレクションからその参照を取得します。

### プロトタイプ

```c
const struct aws_profile *aws_profile_collection_get_profile( const struct aws_profile_collection *profile_collection, const struct aws_string *profile_name);
```
