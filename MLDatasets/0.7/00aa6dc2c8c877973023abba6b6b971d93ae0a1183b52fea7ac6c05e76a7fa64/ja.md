```
Iris(; as_df = true, dir = nothing)
```

フィッシャーの古典的なアイリスデータセット。

アイリスの3つの異なる種からの測定値：セトサ、バージカラー、バージニカ。それぞれの種の例は50個あります。

各例には4つの測定値があります：がくの長さ、がくの幅、花弁の長さ、花弁の幅。測定値はセンチメートル単位です。

このモジュールは、[UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/iris)からデータを取得します。

注意：このデータセットには事前に定義されたトレイン-テスト分割はありません。

# 引数

  * `as_df = true`の場合、データをプレーン配列ではなくデータフレームとしてロードします。
  * 特定の`dir`を渡すことでデータセットをロードまたはダウンロードする場所を指定できます。そうでない場合はデフォルトの場所を使用します。

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
julia> dataset = Iris()
Iris:
  metadata => Dict{String, Any} with 4 entries
  features => 150×4 DataFrame
  targets => 150×1 DataFrame
  dataframe => 150×5 DataFrame


julia> dataset[1:2]
(2×4 DataFrame
 Row │ sepallength  sepalwidth  petallength  petalwidth 
     │ Float64      Float64     Float64      Float64    
─────┼──────────────────────────────────────────────────
   1 │         5.1         3.5          1.4         0.2
   2 │         4.9         3.0          1.4         0.2, 2×1 DataFrame
 Row │ class       
     │ String15    
─────┼─────────────
   1 │ Iris-setosa
   2 │ Iris-setosa)

julia> X, y = Iris(as_df=false)[:]
([5.1 4.9 … 6.2 5.9; 3.5 3.0 … 3.4 3.0; 1.4 1.4 … 5.4 5.1; 0.2 0.2 … 2.3 1.8], InlineStrings.String15["Iris-setosa" "Iris-setosa" … "Iris-virginica" "Iris-virginica"])
```
