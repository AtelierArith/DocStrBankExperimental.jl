```
CIFAR100(; Tx=Float32, split=:train, dir=nothing)
CIFAR100([Tx, split])
```

CIFAR100データセットは、8000万の小さな画像データセットのラベル付きサブセットです。100クラスと20のスーパークラスに分かれた60000枚の32x32カラー画像で構成されており、各クラスには600枚の画像があります。

指定された`indices`に対応するCIFAR-100 **トレーニングセット**のラベル（粗いラベルと細かいラベル）を、2つの`Int`または2つの`Vector{Int}`のタプルとして返します。返される変数は、それぞれ粗いラベル（`Yc`）と細かいラベル（`Yf`）です。

# 引数

  * データセットをロードまたはダウンロードする特定の`dir`を指定できます。指定しない場合はデフォルトのものが使用されます。
  * `split`: データパーティションを選択します。`:train`または`:test`の値を取ることができます。

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
julia> dataset = CIFAR100()
CIFAR100:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :train
  features    =>    32×32×3×50000 Array{Float32, 4}
  targets     =>    (coarse = "50000-element Vector{Int64}", fine = "50000-element Vector{Int64}")

julia> dataset[1:5].targets
(coarse = [11, 15, 4, 14, 1], fine = [19, 29, 0, 11, 1])

julia> X, y = dataset[:];

julia> dataset.metadata
Dict{String, Any} with 3 entries:
  "n_observations"     => 50000
  "class_names_coarse" => ["aquatic_mammals", "fish", "flowers", "food_containers", "fruit_and_vegetables", "household_electrical_devices", "household_furniture", "insects", "large_carnivores", "large_man-made_…
  "class_names_fine"   => ["apple", "aquarium_fish", "baby", "bear", "beaver", "bed", "bee", "beetle", "bicycle", "bottle"  …  "train", "trout", "tulip", "turtle", "wardrobe", "whale", "willow_tree", "wolf", "w…
```
