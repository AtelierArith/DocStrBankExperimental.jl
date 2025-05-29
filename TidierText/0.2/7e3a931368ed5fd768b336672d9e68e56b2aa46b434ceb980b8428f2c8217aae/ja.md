```
@unnest_ngrams(df, output_col, input_col, n, to_lower = false)
```

`df`の`input_col`にあるテキストからn-グラムを作成し、結果を`output_col`に出力します。

# 引数

  * `df`: 入力DataFrame。
  * `output_col`: n-グラムを格納する出力列の名前。
  * `input_col`: テキストを含む入力列の名前。
  * `n`: n-グラムのサイズ。
  * `to_lower`: テキストを分割する前に小文字に変換するかどうかを示すオプションのブール値で、デフォルトはfalse。
  * `strip_non_alphanum`: 非英数字の文字を削除するオプションのブール値で、デフォルトはtrue。

# 戻り値

  * n-グラムを含む新しいDataFrame。

# 例

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              text = ["The quick brown fox jumps.",
                      "The sun rises in the east."],
                      doc = [1, 2]
            );

julia> @unnest_ngrams(df, term, text, 2, to_lower = false)
9×2 DataFrame
 Row │ doc    term        
     │ Int64  String      
─────┼────────────────────
   1 │     1  The quick
   2 │     1  quick brown
   3 │     1  brown fox
   4 │     1  fox jumps
   5 │     2  The sun
   6 │     2  sun rises
   7 │     2  rises in
   8 │     2  in the
   9 │     2  the east

julia> @unnest_ngrams(df, term, text, 2)
9×2 DataFrame
 Row │ doc    term        
     │ Int64  String      
─────┼────────────────────
   1 │     1  The quick
   2 │     1  quick brown
   3 │     1  brown fox
   4 │     1  fox jumps
   5 │     2  The sun
   6 │     2  sun rises
   7 │     2  rises in
   8 │     2  in the
   9 │     2  the east   
```
