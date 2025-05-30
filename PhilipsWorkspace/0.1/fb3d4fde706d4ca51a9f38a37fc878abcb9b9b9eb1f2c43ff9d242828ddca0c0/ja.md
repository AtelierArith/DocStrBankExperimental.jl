```
get_parameter_value(name, workspace)
```

指定された名前のパラメータの値をワークスペースから取得します。

パラメータの値は通常、単一の要素を持つ配列として保存されているため、再帰的に `only` を適用して「アンラップ」します。

# 引数

  * `name::String`: パラメータの名前。
  * `workspace::Workspace`: パラメータを含むワークスペース。

# 戻り値

パラメータの「アンラップ」された値。

# 例

```
EX_PROTO_scan_enable = get_parameter_value("EX_PROTO_scan_enable", workspace)
```
