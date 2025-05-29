```
create_matrix_templates(shapes::Vector{Vector{Int64}}, template_type::String)
```

指定された形状ベクトルとテンプレートタイプに基づいて多次元テンプレートを作成します。テンプレートは均一、ランダム、またはゼロで埋められたものが可能です。

# 引数

  * `shapes::Vector{Vector{Int64}}`: 作成するテンプレートの各次元を表すベクトルのベクトル。
  * `template_type::String`: 作成するテンプレートのタイプ。 "uniform"（デフォルト）、"random"、または "zeros" のいずれかです。

# 戻り値

  * 入力ベクトルで指定された多次元形状を持つ配列のベクトル。
