```
SpatialDispersion <: OutcomeSpace
SpatialDispersion(stencil, x::AbstractArray;
    periodic = true,
    c = 5,
    skip_encoding = false,
    L = nothing,
)
```

高次元配列の入力データに対して[`Dispersion`](@ref)を一般化した、分散ベースの[`OutcomeSpace`](@ref)です。

`SpatialDispersion`は[Azami2019](@citet)の2D正方形分散（シャノン）エントロピー推定器に基づいていますが、ここでは`N`次元の入力データ`x`に対して、任意の近傍領域（ステンシル）と（オプションで）周期境界条件を持つ純粋な確率推定器として実装されています。

[`information`](@ref)および[`information_normalized`](@ref)と組み合わせることで、この確率推定器を使用して、任意のタイプの（正規化された）一般化空間時間分散[`InformationMeasure`](@ref)を計算できます。

## 引数

  * `stencil`。各ハイパーボクセル（すなわち2Dのピクセル）周辺に含めるローカルエリア（ハイパーレクタングル）またはこのエリア内のポイントを定義します。以下の例では、ステンシルを指定するさまざまな方法を示しています。詳細については、[`SpatialOrdinalPatterns`](@ref)を参照してください。ステンシルに関する詳細情報は[`SpatialOrdinalPatterns`](@ref)を参照してください。
  * `x::AbstractArray`。入力データ。最適化と境界チェックのためにそのサイズを知る必要があるため、提供する必要があります。

## キーワード引数

  * `periodic::Bool`。`periodic == true`の場合、ステンシルは配列の端でラップする必要があります。`periodic = false`の場合、ステンシルが配列の境界を超えるピクセルはスキップされます。
  * `c::Int`。ガウスエンコーディングに使用する離散カテゴリの数を決定します。
  * `skip_encoding`。`skip_encoding == true`の場合、`encoding`は無視され、分散パターンは`x`から直接計算されます。このとき、`L`は`x`のアルファベットの長さであると仮定されます（カテゴリカルまたは整数データに便利です）。したがって、`skip_encoding == true`の場合、`L`も指定する必要があります。これはカテゴリカルまたは整数値データに便利です。
  * `L`。`L == nothing`（デフォルト）の場合、総結果の数は`stencil`と`encoding`から推測されます。`L`が整数に設定されている場合、データは事前にエンコードされていると見なされ、総結果の数は`L`に設定されます。

## アウトカムスペース

`SpatialDispersion`のアウトカムスペースは、要素がガウスCDFによってエンコードされた記号（整数）であるユニークな遅延ベクトルです。したがって、アウトカムスペースは、要素がすべて`1:c`の可能な値であるすべての`m`次元の遅延ベクトルです。そのようなベクトルは`c^m`個あります。

## 説明

高次元データから確率/エントロピーを推定することは概念的には簡単です。

1. 提供された`encoding`スキームを使用して、`x`内のすべての他の値`xᵢ ∈ x`に対して各値（ハイパーボクセル）を離散化します。
2. `stencil`を使用して、各ハイパーボクセルの周りの関連する（離散化された）ポイントを抽出します。
3. これらのポイントから記号を構築します。
4. 記号の合計正規化ヒストグラムを確率分布として取ります。
5. オプションで、この確率分布から[`information`](@ref)または[`information_normalized`](@ref)を計算します。

## 使用法

ステンシルを指定する3つの異なる方法を使用して、空間分散エントロピーを計算する方法は次のとおりです。

```julia
x = rand(50, 50) # 空間システムの進化の最初の「時間スライス」

# カルテジアンステンシル
stencil_cartesian = CartesianIndex.([(0,0), (1,0), (1,1), (0,1)])
est = SpatialDispersion(stencil_cartesian, x)
information_normalized(est, x)

# エクステント/ラグステンシル
extent = (2, 2); lag = (1, 1); stencil_ext_lag = (extent, lag)
est = SpatialDispersion(stencil_ext_lag, x)
information_normalized(est, x)

# マトリックスステンシル
stencil_matrix = [1 1; 1 1]
est = SpatialDispersion(stencil_matrix, x)
information_normalized(est, x)
```

この方法を空間データの時系列に適用するには、単に呼び出しをループ（ブロードキャスト）します。例えば：

```julia
imgs = [rand(50, 50) for i = 1:100]; # 100秒間に1秒ごとの1つの画像
stencil = ((2, 2), (1, 1)) # 2x2のステンシル（すなわち長さ4の分散パターン）
est = SpatialDispersion(stencil, first(imgs))
h_vs_t = information_normalized.(Ref(est), imgs)
```

一般化空間時間分散エントロピーを計算することは簡単です。例えば、[`Renyi`](@ref)を使用して：

```julia
x = reshape(repeat(1:5, 500) .+ 0.1*rand(500*5), 50, 50)
est = SpatialDispersion(stencil, x)
information(Renyi(q = 2), est, x)
```

他にも、[`SpatialOrdinalPatterns`](@ref)、[`GaussianCDFEncoding`](@ref)、[`codify`](@ref)を参照してください。 ```
