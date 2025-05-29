```
Titanic(; as_df = true, dir = nothing)
```

タイタニックのデータセットで、タイタニック号の乗客の生存について説明しています。

# 引数

  * `as_df = true` の場合、データをプレーン配列ではなくデータフレームとして読み込みます。
  * 特定の `dir` を渡すことができ、そこにデータセットを読み込むかダウンロードします。そうでなければ、デフォルトのものを使用します。

# フィールド

  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データの特徴。`as_df=false` の場合は配列、それ以外の場合はデータフレーム。
  * `targets`: 教師あり学習のためのターゲット。`as_df=false` の場合は配列、それ以外の場合はデータフレーム。
  * `dataframe`: `features` と `targets` の両方を含むデータフレーム。`as_df=false` の場合は `nothing`、それ以外の場合はデータフレームです。

# メソッド

  * `dataset[i]`: 観測値 `i` を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測値の数。

# 例

```julia-repl
julia> using MLDatasets: Titanic

julia> using DataFrames

julia> dataset = Titanic()
Titanic:
  metadata => Dict{String, Any} with 5 entries
  features => 891×11 DataFrame
  targets => 891×1 DataFrame
  dataframe => 891×12 DataFrame


julia> describe(dataset.dataframe)
12×7 DataFrame
 Row │ variable     mean      min                  median   max                          nmissing  eltype                   
     │ Symbol       Union…    Any                  Union…   Any                          Int64     Type                     
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ PassengerId  446.0     1                    446.0    891                                 0  Int64
   2 │ Survived     0.383838  0                    0.0      1                                   0  Int64
   3 │ Pclass       2.30864   1                    3.0      3                                   0  Int64
   4 │ Name                   Abbing, Mr. Anthony           van Melkebeke, Mr. Philemon         0  String
   5 │ Sex                    female                        male                                0  String7
   6 │ Age          29.6991   0.42                 28.0     80.0                              177  Union{Missing, Float64}
   7 │ SibSp        0.523008  0                    0.0      8                                   0  Int64
   8 │ Parch        0.381594  0                    0.0      6                                   0  Int64
   9 │ Ticket                 110152                        WE/P 5735                           0  String31
  10 │ Fare         32.2042   0.0                  14.4542  512.329                             0  Float64
  11 │ Cabin                  A10                           T                                 687  Union{Missing, String15}
  12 │ Embarked               C                             S                                   2  Union{Missing, String1}
```
