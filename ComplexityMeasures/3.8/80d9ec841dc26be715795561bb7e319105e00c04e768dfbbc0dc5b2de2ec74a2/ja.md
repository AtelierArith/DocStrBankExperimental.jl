```
SpatialBubbleSortSwaps <: SpatialOutcomeSpace
SpatialBubbleSortSwaps(stencil, x; periodic = true)
```

`SpatialBubbleSortSwaps` は [`BubbleSortSwaps`](@ref) を高次元配列に一般化し、バブルソートアルゴリズムがそれらをソートするために必要なスワップ操作の数をピクセル/ボクセル/ハイパーボクセルウィンドウの観点からエンコードします。

これは何を意味するのでしょうか？ [`BubbleSortSwaps`](@ref) の場合、入力データは埋め込み次元 `m` を使用して埋め込まれ、必要なスワップの数は各埋め込みベクトルに対して計算されます。 `SpatialBubbleSortSwaps` の場合、"埋め込み次元" `m` は `stencil` の要素数から推測され、"埋め込みベクトル" は `stencil` によって選択されたハイパーボクセルです。

## アウトカム空間

`SpatialBubbleSortSwaps` のアウトカム空間 `Ω` は、特定のピクセル/ボクセル/ハイパーボクセルウィンドウをソートするためにバブルソートアルゴリズムが必要とするスワップの数に対応する整数の範囲 `0:(n*(n-1)÷2)` です。

## 引数

  * `stencil`。各ハイパーボクセル（すなわち2Dのピクセル）周辺に含めるローカルエリア（ハイパーレクタングル）またはこのエリア内のどのポイントを定義します。ステンシルに関する詳細情報や指定方法の例については、[`SpatialOrdinalPatterns`](@ref) および [`SpatialDispersion`](@ref) を参照してください。
  * `x::AbstractArray`。入力データ。最適化と境界チェックのためにそのサイズを知る必要があるため、提供する必要があります。

## キーワード引数

  * `periodic::Bool`。`periodic == true` の場合、ステンシルは配列の端でラップする必要があります。`periodic = false` の場合、配列の境界を超えるステンシルを持つピクセルはスキップされます。

## 例

```julia
using ComplexityMeasures
using Random; rng = MersenneTwister(1234)

x = rand(rng, 100, 100, 100) # いくつかの3D画像
stencil = zeros(Int,2,2,2) # 3Dステンシル
stencil[:, :, 1] = [1 0; 1 1]
stencil[:, :, 2] = [0 1; 1 0]
o = SpatialBubbleSortSwaps(stencil, x)

# ボクセルウィンドウ間の「バブルソートの複雑さ」の分布
counts_and_outcomes(o, x)

# 縮小調整された確率を持つ「空間バブルカニアダキスエントロピー」
information(Kaniadakis(), Shrinkage(), o, x)
```
