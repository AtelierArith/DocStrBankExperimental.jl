```
Conv(filter, in => out, σ = identity;
     stride = 1, pad = 0, dilation = 1, groups = 1, [bias, init])
Conv(weight, [bias, activation; stride, pad, dilation])
```

標準的な畳み込み層です。`filter`は畳み込みカーネルのサイズを指定する整数のタプルであり、`in`と`out`は入力チャネルと出力チャネルの数を指定します。

画像データはWHCN順（幅、高さ、チャネル、バッチ）で保存する必要があります。言い換えれば、100×100のRGB画像は`100×100×3×1`の配列であり、50のバッチは`100×100×3×50`の配列になります。これは`N = 2`の空間次元を持ち、(5,5)のようなカーネルサイズが必要です。これは整数の2タプルです。

`N`の特徴次元に沿って畳み込みを行うために、この層は`ndims(x) == N+2`の配列を入力として期待します。ここで、`size(x, N+1) == in`は入力チャネルの数であり、`size(x, ndims(x))`は（常に通り）バッチ内の観測数です。次に：

  * `filter`は`N`個の整数のタプルである必要があります。
  * キーワード`stride`と`dilation`はそれぞれ単一の整数、または`N`個の整数を持つタプルである必要があります。
  * キーワード`pad`はデータ配列の境界に追加される要素の数を指定します。これは以下のいずれかです。

      * 周囲に均等にパディングするための単一の整数、
      * 各空間次元の始まり/終わりに同じパディングを適用するための`N`個の整数のタプル、
      * 非対称パディングのための`2*N`個の整数のタプル、または
      * `SamePad()`の単一要素で、`size(output,d) == size(x,d) / stride`（おそらく丸められた）となるようにパディングを計算します。
  * キーワード`groups`は`Int`であることが期待されます。これは畳み込みを分割するグループの数を指定します。

層の初期化を制御するためのキーワード：

  * `init` - 初期重みを生成するために使用される関数。デフォルトは`glorot_uniform`です。
  * `bias` - 初期バイアスベクトルはデフォルトで全てゼロです。トレーニング可能なバイアスは、これを`false`に設定することで完全に無効にすることができ、または`bias = randn(Float32, out)`のように別のベクトルを提供することができます。

コンストラクタの2番目の形式では、事前に構築された重み行列とバイアスベクトルを渡すことができます。これは、重みを自分で初期化したい場合に便利です。

[`ConvTranspose`](@ref)、[`DepthwiseConv`](@ref)、[`CrossCor`](@ref)も参照してください。

# 例

```jldoctest
julia> xs = rand(Float32, 100, 100, 3, 50); # 50のRGB画像のバッチ

julia> layer = Conv((5,5), 3 => 7, relu; bias = false)
Conv((5, 5), 3 => 7, relu, bias=false)  # 525パラメータ

julia> layer(xs) |> size
(96, 96, 7, 50)

julia> Conv((5,5), 3 => 7; stride = 2)(xs) |> size
(48, 48, 7, 50)

julia> Conv((5,5), 3 => 7; stride = 2, pad = SamePad())(xs) |> size
(50, 50, 7, 50)

julia> Conv((1,1), 3 => 7; pad = (20,10,0,0))(xs) |> size
(130, 100, 7, 50)

julia> Conv((5,5), 3 => 7; stride = 2, dilation = 4)(xs) |> size
(42, 42, 7, 50)
```

```jldoctest
julia> weight = rand(Float32, 3, 4, 5);

julia> bias = zeros(Float32, 5);

julia> layer = Conv(weight, bias, sigmoid)  # 1つの空間次元を期待
Conv((3,), 4 => 5, σ)  # 65パラメータ

julia> layer(randn(Float32, 100, 4, 64)) |> size
(98, 5, 64)

julia> Flux.trainables(layer) |> length
2
```
