```
MNIST(; Tx=Float32, split=:train, dir=nothing)
MNIST([Tx, split])

手書き数字のMNISTデータベース。

  * 著者: Yann LeCun, Corinna Cortes, Christopher J.C. Burges
  * ウェブサイト: http://yann.lecun.com/exdb/mnist/

MNISTは、小規模な機械学習実験でよく使用される古典的な画像分類データセットです。70,000枚の手書き数字の画像が含まれています。各観測は、10の可能な数字（0-9）のうちの1つの手書きバージョンを示す28x28ピクセルのグレースケール画像です。

# 引数

  * データセットをロードまたはダウンロードする特定の`dir`を渡すことができます。そうでなければ、デフォルトのものが使用されます。
  * `split`: データパーティションを選択します。`：train`または`：test`の値を取ることができます。

# フィールド

  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データ特徴を格納する配列。
  * `targets`: 教師あり学習のためのターゲットを格納する配列。
  * `split`.

# メソッド

  * `dataset[i]`: 観測値`i`を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測の数。
  * [`convert2image`](@ref)は特徴を`Gray`画像に変換します。

# 例

画像は、eltype `Tx`の多次元配列としてロードされます。`Tx <: Integer`の場合、すべての値は`0`から`255`の範囲内になります。そうでなければ、値は`0`から`1`の間にスケーリングされます。`MNIST().features`は3D配列（すなわち`Array{Tx,3}`）で、WHN形式（幅、高さ、画像数）です。ラベルは`MNIST().targets`の整数ベクトルとして格納されます。

```

julia-repl julia> using MLDatasets: MNIST

julia> dataset = MNIST(:train) MNIST:   metadata    =>    Dict{String, Any} with 3 entries   split       =>    :train   features    =>    28×28×60000 Array{Float32, 3}   targets     =>    60000-element Vector{Int64}

julia> dataset[1:5].targets 5-element Vector{Int64}: 7 2 1 0 4

julia> X, y = dataset[:];

julia> dataset = MNIST(UInt8, :test) MNIST:   metadata    =>    Dict{String, Any} with 3 entries   split       =>    :test   features    =>    28×28×10000 Array{UInt8, 3}   targets     =>    10000-element Vector{Int64} ```
