```
Omniglot(; Tx=Float32, split=:train, dir=nothing)
Omniglot([Tx, split])
```

ワンショット学習のためのOmniglotデータセット

  * 著者: Brenden M. Lake, Ruslan Salakhutdinov, Joshua B. Tenenbaum
  * ウェブサイト: https://github.com/brendenlake/omniglot

Omniglotデータセットは、より人間に似た学習アルゴリズムを開発するために設計されています。50の異なるアルファベットから1623種類の異なる手書き文字が含まれています。1623の各文字は、20人の異なる人々によってAmazonのMechanical Turkを通じてオンラインで描かれました。各画像は、ミリ秒単位の時間(t)を持つ[x,y,t]座標のシーケンスであるストロークデータとペアになっています。

# 引数

  * データセットをロードまたはダウンロードするための特定の`dir`を渡すことができます。そうでなければ、デフォルトのものが使用されます。
  * `split`: データパーティションを選択します。値は`:train`、`:test`、`:small1`、または`:small2`を取ることができます。

# フィールド

  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データ特徴を格納する配列。
  * `targets`: 教師あり学習のためのターゲットを格納する配列。
  * `split`.

# メソッド

  * `dataset[i]`: 観測値`i`を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測値の数。
  * [`convert2image`](@ref)は特徴を`Gray`画像に変換します。

# 例

画像はeltype `Tx`の多次元配列としてロードされます。すべての値は`0`または`1`になります。`Omniglot().features`は3D配列（すなわち`Array{Tx,3}`）で、WHN形式（幅、高さ、画像数）です。ラベルは`Omniglot().targets`の文字列ベクトルとして格納されています。

```julia-repl
julia> using MLDatasets: Omniglot

julia> dataset = Omniglot(:train)
Omniglot:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :train
  features    =>    105×105×19280 Array{Float32, 3}
  targets     =>    19280-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{String}:
 "Arcadian"
 "Arcadian"
 "Arcadian"
 "Arcadian"
 "Arcadian"

julia> X, y = dataset[:];

julia> dataset = Omniglot(UInt8, :test)
Omniglot:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :test
  features    =>    105×105×13180 Array{UInt8, 3}
  targets     =>    13180-element Vector{Int64}
```
