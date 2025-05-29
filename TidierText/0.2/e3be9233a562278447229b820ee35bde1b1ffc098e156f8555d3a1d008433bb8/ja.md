```
@bind_tf_idf(df, term_col, document_col, n)
```

指定された `df` の列に対して TF-IDF 値を計算します。

# 引数

  * `df`: 入力 DataFrame。
  * `term_col`: 用語を含む列。
  * `document_col`: 文書識別子を含む列。
  * `n`: 用語頻度を含む列。

# 戻り値

  * TF、IDF、および TF-IDF 値を含む新しい DataFrame。

# 例

```jldoctest
julia> using DataFrames;
       df = DataFrame(
              doc_id = [1, 1, 2, 2, 3, 3],
              term = ["apple", "banana", "apple", "cherry", "banana", "date"],
              n = [1, 4, 6, 4, 9, 8]
            );

julia> @bind_tf_idf(df, doc_id, term, n)
6×6 DataFrame
 Row │ doc_id  term    n      tf        idf       tf_idf   
     │ Int64   String  Int64  Float64   Float64   Float64  
─────┼─────────────────────────────────────────────────────
   1 │      1  apple       1  0.142857  0.693147  0.099021
   2 │      1  banana      4  0.307692  0.693147  0.213276
   3 │      2  apple       6  0.857143  0.693147  0.594126
   4 │      2  cherry      4  1.0       0.693147  0.693147
   5 │      3  banana      9  0.692308  0.693147  0.479871
   6 │      3  date        8  1.0       0.693147  0.693147
```
