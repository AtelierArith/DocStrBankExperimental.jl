```
aws_profile_property_get_sub_property(property, sub_property_name)
```

指定された名前のサブプロパティの値への参照を返します。プロパティ内に存在する場合。

### プロトタイプ

```c
const struct aws_string *aws_profile_property_get_sub_property( const struct aws_profile_property *property, const struct aws_string *sub_property_name);
```
