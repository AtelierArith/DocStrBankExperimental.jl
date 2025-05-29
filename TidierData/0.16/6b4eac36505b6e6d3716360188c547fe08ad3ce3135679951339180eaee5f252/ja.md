```
@anti_join(df1, df2, [by])
```

`df1` と `df2` に対してオプションの `by` を使用してアンチジョインを実行します。

# 引数

  * `df1`: DataFrame。
  * `df2`: DataFrame。
  * `by`: オプションの列または列のタプル。`by` は個々の列の補間をサポートします。`by` が指定されていない場合、`df1` と `df2` の間で共有される列の名前から推測されます。

# 例

```jldoctest
julia> df1 = DataFrame(a = ["a", "b"], b = 1:2);

julia> df2 = DataFrame(a = ["a", "c"], c = 3:4);
  
julia> @anti_join(df1, df2)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, a)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, a = a)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, "a")
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, "a" = "a")
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2
```
