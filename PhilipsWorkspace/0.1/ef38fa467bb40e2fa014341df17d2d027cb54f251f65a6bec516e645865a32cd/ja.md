```
get_object(type, instance, workspace)
```

特定のオブジェクトインスタンスの属性名と値をワークスペースから抽出します。

# 引数

  * `type::String`: オブジェクトのタイプ（例: "GR", "RF", "SQ"）。
  * `instance::String`: オブジェクトのインスタンス（例: "s_ex", "ex", "base"）。
  * `workspace::Workspace`: GOALワークスペース。

# 戻り値

属性名をシンボルとして、属性値を持つ名前付きタプル。

# 例

```
GR_s_ex = get_object("GR", "s_ex", workspace)
GR_s_ex.str
```
