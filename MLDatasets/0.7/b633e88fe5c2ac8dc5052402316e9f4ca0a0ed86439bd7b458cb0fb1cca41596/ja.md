```
BostonHousing(; as_df = true, dir = nothing)
```

古典的なボストン住宅の表形式データセット。

出典:    (a) 出所:  このデータセットはカーネギーメロン大学で維持されているStatLibライブラリから取得されました。    (b) 作成者:  Harrison, D. と Rubinfeld, D.L. 'ヘドニック価格と清浄な空気の需要', J. Environ. Economics & Management,                  vol.5, 81-102, 1978.    (c) 日付: 1993年7月7日

インスタンス数: 506

属性数: 13の連続属性（ターゲット属性「MEDV」を含む）、1つのバイナリ値属性。

# 引数

  * `as_df = true`の場合、データをプレーン配列ではなくデータフレームとして読み込みます。
  * 特定の`dir`を渡すことでデータセットを読み込むかダウンロードする場所を指定できます。指定しない場合はデフォルトの場所を使用します。

# フィールド

  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データの特徴。`as_df=false`の場合は配列、それ以外の場合はデータフレーム。
  * `targets`: 教師あり学習のためのターゲット。`as_df=false`の場合は配列、それ以外の場合はデータフレーム。
  * `dataframe`: `features`と`targets`の両方を含むデータフレーム。`as_df=false`の場合は`nothing`、それ以外の場合はデータフレームです。

# メソッド

  * `dataset[i]`: 観測値`i`を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測値の数。

# 例

```julia-repl
julia> using MLDatasets: BostonHousing

julia> dataset = BostonHousing()
BostonHousing:
  metadata => Dict{String, Any} with 5 entries
  features => 506×13 DataFrame
  targets => 506×1 DataFrame
  dataframe => 506×14 DataFrame


julia> dataset[1:5][1]
5×13 DataFrame
 Row │ CRIM     ZN       INDUS    CHAS   NOX      RM       AGE      DIS      RAD    TAX    PTRATIO  B        LSTAT   
     │ Float64  Float64  Float64  Int64  Float64  Float64  Float64  Float64  Int64  Int64  Float64  Float64  Float64 
─────┼───────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 0.00632     18.0     2.31      0    0.538    6.575     65.2   4.09        1    296     15.3   396.9      4.98
   2 │ 0.02731      0.0     7.07      0    0.469    6.421     78.9   4.9671      2    242     17.8   396.9      9.14
   3 │ 0.02729      0.0     7.07      0    0.469    7.185     61.1   4.9671      2    242     17.8   392.83     4.03
   4 │ 0.03237      0.0     2.18      0    0.458    6.998     45.8   6.0622      3    222     18.7   394.63     2.94
   5 │ 0.06905      0.0     2.18      0    0.458    7.147     54.2   6.0622      3    222     18.7   396.9      5.33

julia> dataset[1:5][2]
5×1 DataFrame
Row │ MEDV    
    │ Float64 
────┼─────────
  1 │    24.0
  2 │    21.6
  3 │    34.7
  4 │    33.4
  5 │    36.2  

julia> X, y = BostonHousing(as_df=false)[:]
([0.00632 0.02731 … 0.10959 0.04741; 18.0 0.0 … 0.0 0.0; … ; 396.9 396.9 … 393.45 396.9; 4.98 9.14 … 6.48 7.88], [24.0 21.6 … 22.0 11.9])
```
