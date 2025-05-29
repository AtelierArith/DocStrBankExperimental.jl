```
@unnest_regex(df, output_col, input_col, pattern = "\s+", to_lower = false)
```

`df`の`input_col`内のテキストを正規表現`pattern`に基づいて分割し、結果を`output_col`に出力します。

# 引数

  * `df`: 入力データフレーム。
  * `output_col`: 結果を格納する出力列の名前。
  * `input_col`: 分割するテキストを含む入力列の名前。
  * `pattern`: テキストを分割するために使用する正規表現パターン。
  * `to_lower`: 分割前にテキストを小文字に変換するかどうかを示すオプションのブール値で、デフォルトはfalseです。
  * `strip_non_alphanum`: 非英数字文字を削除するオプションのブール値で、デフォルトはtrueです。

# 戻り値

  * 正規表現パターンに基づいてテキストが分割された新しいデータフレーム。

# 例

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick brown fox jumps.",
                      "One column and the one row?"],
                      doc = [1, 2]
            );

julia> @unnest_regex(df, word, text, "the")
3×2 DataFrame
 Row │ doc    word                      
     │ Int64  SubStrin…                 
─────┼──────────────────────────────────
   1 │     1  The quick brown fox jumps
   2 │     2  One column and
   3 │     2  one row

julia> @unnest_regex(df, word, text, "the", to_lower = true, strip_non_alphanum = false)
3×2 DataFrame
 Row │ doc    word                   
     │ Int64  SubStrin…              
─────┼───────────────────────────────
   1 │     1  quick brown fox jumps.
   2 │     2  one column and
   3 │     2  one row?
```
