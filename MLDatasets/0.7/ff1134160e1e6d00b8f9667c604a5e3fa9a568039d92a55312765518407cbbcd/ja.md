```
EMNIST(name; Tx=Float32, split=:train, dir=nothing)
EMNIST(name, [Tx, split])
```

EMNISTデータセットは、NIST特別データベース19（https://www.nist.gov/srd/nist-special-database-19）から派生した手書きの文字数字のセットであり、MNISTデータセット（http://yann.lecun.com/exdb/mnist/）に直接一致する28x28ピクセルの画像形式とデータセット構造に変換されています。データセットの内容と変換プロセスに関するさらなる情報は、https://arxiv.org/abs/1702.05373v1で入手可能な論文に記載されています。

# 引数

  * `name`: EMNISTデータセットの名前。可能な値は `:balanced, :byclass, :bymerge, :digits, :letters, :mnist` です。
  * `split`: データパーティションを選択します。値は `:train` または `:test` を取ることができます。
  * 特定の `dir` を渡すことでデータセットをロードまたはダウンロードする場所を指定できます。指定しない場合はデフォルトの場所が使用されます。

# フィールド

  * `name`.
  * `split`.
  * `metadata`: データセットに関する追加情報を含む辞書。
  * `features`: データの特徴を格納する配列。
  * `targets`: 教師あり学習のためのターゲットを格納する配列。

# メソッド

  * `dataset[i]`: 観測値 `i` を特徴とターゲットの名前付きタプルとして返します。
  * `dataset[:]`: すべての観測値を特徴とターゲットの名前付きタプルとして返します。
  * `length(dataset)`: 観測値の数。
  * [`convert2image`](@ref) は特徴を `Gray` 画像に変換します。

# 例

画像は、eltype `Tx` の多次元配列としてロードされます。もし `Tx <: Integer` であれば、すべての値は `0` と `255` の間になります。そうでなければ、値は `0` と `1` の間にスケーリングされます。`EMNIST().features` は3D配列（すなわち `Array{Tx,3}`）で、WHN形式（幅、高さ、画像数）です。ラベルは `EMNIST().targets` に整数のベクトルとして格納されています。

```julia-repl
julia> using MLDatasets: EMNIST

julia> dataset = EMNIST(:letters, split=:train)
EMNIST:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :train
  features    =>    28×28×60000 Array{Float32, 3}
  targets     =>    60000-element Vector{Int64}

julia> dataset[1:5].targets
5-element Vector{Int64}:
7
2
1
0
4

julia> X, y = dataset[:];

julia> dataset = EMNIST(:balanced, Tx=UInt8, split=:test)
EMNIST:
  metadata    =>    Dict{String, Any} with 3 entries
  split       =>    :test
  features    =>    28×28×10000 Array{UInt8, 3}
  targets     =>    10000-element Vector{Int64}
```
