```
CIFAR10(; Tx=Float32, split=:train, dir=nothing)
CIFAR10([Tx, split])
```

CIFAR10データセットは、8000万の小さな画像データセットのラベル付きサブセットです。10クラスに分かれた60000枚の32x32カラー画像で構成されており、各クラスには6000枚の画像があります。

# 引数

  * 特定の`dir`を指定してデータセットを読み込むかダウンロードすることができます。指定しない場合はデフォルトの場所が使用されます。
  * `split`: データのパーティションを選択します。`:train`または`:test`の値を取ることができます。

# フィールド

  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データ特徴を格納する配列。
  * `targets`: 教師あり学習のためのターゲットを格納する配列。
  * `split`.

# メソッド

  * `dataset[i]`: 観測値`i`を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測値の数。
  * [`convert2image`](@ref)は特徴を`RGB`画像に変換します。

# 例

```julia-repl
julia> using MLDatasets: CIFAR10

julia> dataset = CIFAR10()
CIFAR10:
  metadata    =>    Dict{String, Any} with 2 entries
  split       =>    :train
  features    =>    32×32×3×50000 Array{Float32, 4}
  targets     =>    50000-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{Int64}:
 6
 9
 9
 4
 1

julia> X, y = dataset[:];

julia> dataset = CIFAR10(Tx=Float64, split=:test)
CIFAR10:
  metadata    =>    Dict{String, Any} with 2 entries
  split       =>    :test
  features    =>    32×32×3×10000 Array{Float64, 4}
  targets     =>    10000-element Vector{Int64}

julia> dataset.metadata
Dict{String, Any} with 2 entries:
  "n_observations" => 10000
  "class_names"    => ["airplane", "automobile", "bird", "cat", "deer", "dog", "frog", "horse", "ship", "truck"]
```
