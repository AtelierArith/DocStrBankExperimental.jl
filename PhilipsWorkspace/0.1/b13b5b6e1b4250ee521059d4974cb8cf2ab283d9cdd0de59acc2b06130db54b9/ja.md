```
get_parameter_group(group, workspace)
```

特定のグループからワークスペース内のすべてのパラメータを取得します。

# 引数

  * `group::String`: パラメータグループの名前。
  * `workspace::Workspace`: パラメータを含むワークスペース。

# 戻り値

パラメータ名とその値を含む名前付きタプル。

# 例

```
EX_PROTO = get_parameter_group("EX_PROTO", workspace)
EX_PROTO.scan_enable
```
