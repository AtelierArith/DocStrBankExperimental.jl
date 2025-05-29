```
Value(field::Union{String, Symbol}; kwargs...)
```

指定された `field` と追加のキーワード引数を使用して `Value` オブジェクトを構築します。

# 引数

  * `field::Union{String, Symbol}`: `Value` オブジェクトのフィールド名。`String` または `Symbol` のいずれかである必要があります。
  * `kwargs...`: `Value` コンストラクタに渡される追加のキーワード引数。

# 戻り値

指定された `field` とキーワード引数で初期化された `Value` オブジェクト。
