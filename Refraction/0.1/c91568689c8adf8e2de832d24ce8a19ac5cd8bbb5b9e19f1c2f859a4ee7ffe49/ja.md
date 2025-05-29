```
Material(path::String) -> Union{Material, Vector{Material}
```

指定された屈折率データベースのパスから材料を作成します。このメソッドは、指定されたパスがデータベース内の材料に対応していない場合、`ArgumentError`をスローします。

# 引数

  * `path::String` : "<shelf>/<book>/<page>"形式で指定された材料のパス

# 戻り値

  * `Union{Material, Vector{Material}` : 指定されたパスから作成された材料オブジェクト。指定されたパスのページに複数の材料データセットが含まれている場合、メソッドは材料オブジェクトのベクターを返します。
