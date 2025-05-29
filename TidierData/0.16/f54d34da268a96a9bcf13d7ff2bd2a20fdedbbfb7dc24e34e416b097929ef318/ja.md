```
matches(pattern, [flags])
```

`pattern` に一致するすべての列を選択します。

# 引数

  * `pattern`: 文字列。
  * `flags`: フラグを含むオプションの文字列。"i" = 大文字と小文字を区別しないパターンマッチングを行います。"m" = 文字列を複数行として扱います。"s" = 文字列を単一行として扱います。"x" = 正規表現パーサーに、バックスラッシュでエスケープされていないか、文字クラス内にないほとんどの空白を無視するように指示します。これを使用して、正規表現を（わずかに）より読みやすい部分に分割できます。

# 例

```julia
julia> df = DataFrame(a_1 = 1:5, a_2 = 11:15, b_1 = 21:25);

julia> @chain df begin 
         @select(matches("^a"))
       end
5×2 DataFrame
 Row │ a_1    a_2   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15

julia> @chain df begin 
         @select(matches("1$"))
       end
5×2 DataFrame
 Row │ a_1    b_1   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     21
   2 │     2     22
   3 │     3     23
   4 │     4     24
   5 │     5     25

julia> @chain df begin 
         @select(matches("A", "i"))
       end
5×2 DataFrame
 Row │ a_1    a_2   
     │ Int64  Int64 
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14
   5 │     5     15
```
