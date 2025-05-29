```
create_matrix_templates(shapes::Vector{Vector{Int64}})
```

指定された形状ベクトルに基づいて、均一な多次元テンプレートを作成します。

# 引数

  * `shapes::Vector{Vector{Int64}}`: 作成するテンプレートの各次元を表すベクトルのベクトル。

# 戻り値

  * 入力ベクトルで指定された多次元形状を持つ、各々が正規化された配列（均一分布）のベクトル。
