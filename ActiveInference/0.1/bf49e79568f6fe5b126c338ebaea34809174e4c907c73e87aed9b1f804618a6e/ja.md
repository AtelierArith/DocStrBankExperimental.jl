```
create_matrix_templates(shapes::Vector{Int64}, template_type::String)
```

指定された形状ベクトルとテンプレートタイプに基づいてテンプレートを作成します。テンプレートは一様、ランダム、またはゼロで埋められたものにすることができます。

# 引数

  * `shapes::Vector{Int64}`: 作成する各テンプレートの次元を指定するベクトル。
  * `template_type::String`: 作成するテンプレートのタイプ。 "uniform"（デフォルト）、"random"、または "zeros" のいずれかです。

# 戻り値

  * 入力ベクトルによって与えられた形状に対応する配列のベクトル。
