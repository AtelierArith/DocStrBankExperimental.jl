```
@ungroup(df)
```

すべてのグループが削除された `DataFrame` を返します。

これが `GroupedDataFrame` に適用されると、グループ化が解除されます。グループがない `DataFrame` に適用されると、`DataFrame` は変更されずに返されます。

# 引数

  * `df`: `GroupedDataFrame` または `DataFrame` 。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @group_by(a)
       end
GroupedDataFrame with 5 groups based on key: a
First Group (1 row): a = 'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
⋮
Last Group (1 row): a = 'e': ASCII/Unicode U+0065 (category Ll: Letter, lowercase)
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ e         5     15

julia> @chain df begin
         @group_by(a)
         @ungroup
       end
5×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ b         2     12
   3 │ c         3     13
   4 │ d         4     14
   5 │ e         5     15
```
