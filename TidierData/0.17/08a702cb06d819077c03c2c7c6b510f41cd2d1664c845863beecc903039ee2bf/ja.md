```
replace_missing(x, replacement)
```

`x` の `missing` 値を指定された `replacement` 値で置き換えます。

# 引数

  * `x`: 任意の型の入力値。`x` が `missing` の場合、関数は `replacement` を返します。それ以外の場合は、`x` を変更せずに返します。
  * `replacement`: `x` の `missing` を置き換えるための値。

# 例

```jldoctest
julia> df = DataFrame(
              a = [1, missing, 3, 4],
              b = [4, 5, missing, 8]
            );

julia> @chain df begin
         @mutate(a = replace_missing(a, 100),
                 b = replace_missing(b, 35))
       end
4×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      4
   2 │   100      5
   3 │     3     35
   4 │     4      8
```
