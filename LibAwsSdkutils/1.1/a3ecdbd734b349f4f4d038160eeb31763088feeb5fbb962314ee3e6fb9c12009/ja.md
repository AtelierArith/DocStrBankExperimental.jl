```
aws_profile_get_property(profile, property_name)
```

指定された名前のプロパティへの参照を、プロファイルから取得します（存在する場合）。

### プロトタイプ

```c
const struct aws_profile_property *aws_profile_get_property( const struct aws_profile *profile, const struct aws_string *property_name);
```
