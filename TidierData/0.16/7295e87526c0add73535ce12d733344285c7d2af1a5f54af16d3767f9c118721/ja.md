```
@glimpse(df, width = 80)
```

DataFrame（またはGroupedDataFrame）をプレビューします。

`@glimpse`マクロは、DataFrameまたはGroupedDataFrameをプレビューするために使用されます。各列は別々の行に印刷され、そのデータ型と最初のいくつかの要素が表示され、出力は`width`に基づいて切り捨てられます。

# 引数

  * `df`: DataFrameまたはGroupedDataFrame。
  * `width`: 出力の幅、文字数で測定されます。デフォルトは80です。

# 例

```jldoctest
julia> df = DataFrame(
               a = 1:100, 
               b = 1:100, 
               c = repeat(["a"], 100)
               );

julia> @chain df @glimpse
Rows: 100
Columns: 3
.a             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.b             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.c             String         a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a,

julia> @chain df begin
       @group_by(a)
       @glimpse()
       end
Rows: 100
Columns: 3
Groups: a [100]
.a             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.b             Int64          1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15,
.c             String         a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a, a,
```
