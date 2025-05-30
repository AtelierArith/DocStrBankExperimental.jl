```
get_all_objects_of_type(type, workspace)
```

特定のタイプのすべてのオブジェクトをワークスペースから取得します。

# 引数

  * `type::String`: 取得するオブジェクトのタイプ（例："GR", "RF", "SQ"）。
  * `workspace`: オブジェクトを含むワークスペース。

# 戻り値

キーがインスタンスの名前で、値がオブジェクトである名前付きタプル。

# 例

```
GR = get_all_objects_of_type("GR", workspace)
GR.s_ex.str
```
