```
@unnest_tokens(df, output_col, input_col, to_lower = false)
```

`df`の`input_col`にあるテキストを別々の単語にトークン化し、結果を`output_col`に出力します。

# 引数

  * `df`: 入力DataFrame。
  * `output_col`: トークンを格納する出力列の名前。
  * `input_col`: トークン化するテキストを含む入力列の名前。
  * `to_lower`: テキストを分割する前に小文字に変換するかどうかを示すオプションのブール値で、デフォルトはfalseです。
  * `strip_non_alphanum`: 非英数字の文字を削除するオプションのブール値で、デフォルトはtrueです。

# 戻り値

  * トークン化されたテキストを含む新しいDataFrame。

# 例

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick brown fox jumps.",
                      "One column and the one row?"],
                      doc = [1, 2]
            );

julia> @unnest_tokens(df, word, text, strip_non_alphanum = false)
11×2 DataFrame
 Row │ doc    word      
     │ Int64  SubStrin… 
─────┼──────────────────
   1 │     1  The
   2 │     1  quick
   3 │     1  brown
   4 │     1  fox
   5 │     1  jumps.
   6 │     2  One
   7 │     2  column
   8 │     2  and
   9 │     2  the
  10 │     2  one
  11 │     2  row?

julia> @unnest_tokens(df, word, text, to_lower = true)
11×2 DataFrame
 Row │ doc    word      
     │ Int64  SubStrin… 
─────┼──────────────────
   1 │     1  the
   2 │     1  quick
   3 │     1  brown
   4 │     1  fox
   5 │     1  jumps
   6 │     2  one
   7 │     2  column
   8 │     2  and
   9 │     2  the
  10 │     2  one
  11 │     2  row
```
