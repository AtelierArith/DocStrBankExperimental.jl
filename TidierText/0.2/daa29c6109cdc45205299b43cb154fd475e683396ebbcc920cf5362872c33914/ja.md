```
@unnest_characters(df, output_col, input_col, to_lower = false, strip_non_alphanum = true)
```

`df`の`input_col`のテキストを別々の文字に分割し、結果を`output_col`に出力します。

# 引数

  * `df`: 入力DataFrame。
  * `output_col`: 文字を格納する出力列の名前。
  * `input_col`: テキストを含む入力列の名前。
  * `to_lower`: 分割する前にテキストを小文字に変換するかどうかを示すオプションのブール値で、デフォルトはfalseです。
  * `strip_non_alphanum`: 非英数字の文字を削除するオプションのブール値で、デフォルトはtrueです。

# 戻り値

  * 文字に分割されたテキストを持つ新しいDataFrame。

# 例

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick.", "Nice."],
              doc = [1, 2]);

julia> @unnest_characters(df, term, text, to_lower = false, strip_non_alphanum = false)
15×2 DataFrame
 Row │ doc    term 
     │ Int64  Char 
─────┼─────────────
   1 │     1  T
   2 │     1  h
   3 │     1  e
   4 │     1
   5 │     1  q
   6 │     1  u
   7 │     1  i
   8 │     1  c
   9 │     1  k
  10 │     1  .
  11 │     2  N
  12 │     2  i
  13 │     2  c
  14 │     2  e
  15 │     2  .

julia> @unnest_characters(df, term, text, to_lower = true)
13×2 DataFrame
 Row │ doc    term 
     │ Int64  Char 
─────┼─────────────
   1 │     1  t
   2 │     1  h
   3 │     1  e
   4 │     1
   5 │     1  q
   6 │     1  u
   7 │     1  i
   8 │     1  c
   9 │     1  k
  10 │     2  n
  11 │     2  i
  12 │     2  c
  13 │     2  e
```
