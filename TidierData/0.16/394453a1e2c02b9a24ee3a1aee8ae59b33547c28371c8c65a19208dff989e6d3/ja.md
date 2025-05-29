```
missing_if(x, value)
```

特定の `value` を `x` の中で `missing` に置き換えます。

## 引数

  * `x`: 任意の型の入力値。もし `x` がすでに `missing` であるか、`value` と等しい場合、関数は `missing` を返します。それ以外の場合は、`x` を変更せずに返します。
  * `value`: 確認する特定の値。

## 例

```jldoctest
julia> df = DataFrame(
              a = [1, missing, 3, 4],
              b = ["apple", "apple", "banana", "cherry"]
            );

julia> @chain df begin
         @mutate(a = missing_if(a, 4), 
                 b = missing_if(b, "apple"))
       end
4×2 DataFrame
 Row │ a        b       
     │ Int64?   String? 
─────┼──────────────────
   1 │       1  missing 
   2 │ missing  missing 
   3 │       3  banana
   4 │ missing  cherry
```
