```
SVHN2(; Tx=Float32, split=:train, dir=nothing)
SVHN2([Tx, split])
```

ストリートビューの家番号（SVHN）データセット。

  * 著者: Yuval Netzer, Tao Wang, Adam Coates, Alessandro Bissacco, Bo Wu, Andrew Y. Ng
  * ウェブサイト: http://ufldl.stanford.edu/housenumbers

SVHNは、Googleストリートビューの画像にある家番号から取得されました。そのため、方向や画像の背景に関して非常に多様です。MNISTと同様に、SVHNには10のクラス（数字0-9）があり、MNISTとは異なり、データが多く、画像は少し大きい（28x28ではなく32x32）上に追加のRGBカラーチャンネルがあります。このデータセットは、訓練用に73257の数字、テスト用に26032の数字、追加の訓練データとして531131の数字に分割されています。

# 引数

  * データセットを読み込むかダウンロードする特定の`dir`を指定できます。指定しない場合はデフォルトのものが使用されます。
  * `split`: データのパーティションを選択します。`:train`、`:test`、または`:extra`の値を取ることができます。

# フィールド

  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データの特徴を格納する配列。
  * `targets`: 教師あり学習のためのターゲットを格納する配列。
  * `split`.

# メソッド

  * `dataset[i]`: 観測値`i`を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測値の数。
  * [`convert2image`](@ref) は特徴を`RGB`画像に変換します。

# 例

```julia-repl
julia> using MLDatasets: SVHN2

julia> using MLDatasets: SVHN2

julia> dataset = SVHN2()
SVHN2:
  metadata    =>    Dict{String, Any} with 2 entries
  split       =>    :train
  features    =>    32×32×3×73257 Array{Float32, 4}
  targets     =>    73257-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{Int64}:
 1
 9
 2
 3
 2

julia> dataset.metadata
Dict{String, Any} with 2 entries:
  "n_observations" => 73257
  "class_names"    => ["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"]
```
