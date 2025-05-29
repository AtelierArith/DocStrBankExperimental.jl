```
教師
```

時間割における教師を表すための型。

# コンストラクタ

  * `Teacher(name::String, id::String, subjects::Vector{String}, grades::Vector{Int})`

# フィールド

  * `name::String`: 教師の名前。
  * `id::String`: 教師のユニークID。
  * `subjects::Vector{String}`: 教師が教える科目。
  * `grades::Vector{Int}`: 教師が教える学年。
  * `__str__::String`: 教師の事前計算された文字列表現。
