```
Field::AbstractField(
    name::String
    args::Vector{Union{String,Number}}
    sortable::Bool
    no_index::Bool
    as_name::Union{String,Nothing}
)
```

RediSearch スキーマに含める Field オブジェクト。

# 引数

  * `name::String`: フィールドの名前。

# キーワード

  * `args::Vector{Union{String,Number}}`: フィールドの引数のリスト。
  * `sortable::Bool`: ソート可能な状態。
  * `no_index::Bool`: インデックス状態。
  * `as_name::Union{String,Nothing}`: フィールドを参照するための名前。

# 戻り値

  * `Field::AbstractField`
