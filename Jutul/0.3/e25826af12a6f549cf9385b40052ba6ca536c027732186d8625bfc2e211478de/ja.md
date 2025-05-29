```
setup_parameters(model::JutulModel; name = value)
```

指定されたモデルのパラメータストレージを、モデルで定義されたパラメータの値で設定します。

# 引数

  * `name=value`: パラメータの名前とその値。

スカラー（または[`VectorVariables`](@ref)に対して適切なサイズの短いベクトル）は、全ドメインにわたって繰り返されます。一方、エンティティ数（例えば、セル変数のセル数）と等しい長さ（[`VectorVariables`](@ref)に対する列数）のベクトル（または[`VectorVariables`](@ref)に対する行列）は、直接使用されます。
