# DimensionalData

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://rafaqz.github.io/DimensionalData.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://rafaqz.github.io/DimensionalData.jl/dev) ![CI](https://github.com/rafaqz/DimensionalData.jl/workflows/CI/badge.svg) [![Codecov](https://codecov.io/gh/rafaqz/DimensionalData.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/rafaqz/DimensionalData.jl) [![Aqua.jl Quality Assurance](https://img.shields.io/badge/Aqua.jl-%F0%9F%8C%A2-aqua.svg)](https://github.com/JuliaTesting/Aqua.jl)

DimensionalData.jlは、名前付き次元を持つデータセットを扱うためのツールと抽象化を提供し、オプションでルックアップインデックスを提供します。名前付きインデックスのためのコストのかからない抽象化と、高速なインデックスルックアップを提供します。

DimensionalDataは、[AxisArrays.jl](https://github.com/JuliaArrays/AxisArrays.jl)のプラグイン可能で一般化されたバージョンで、よりクリーンな構文とNamedDims.jlに見られる追加機能を備えています。Pythonの[xarray](http://xarray.pydata.org/en/stable/)と似た目標を持ち、主に[Rasters.jl](https://github.com/rafaqz/Rasters.jl)の空間データでの使用のために書かれています。

基本的な構文は次のとおりです：

```julia
julia> using DimensionalData

julia> A = rand(X(50), Y(10.0:40.0))
50×31 DimArray{Float64,2} with dimensions: 
  X,
  Y Sampled{Float64} 10.0:1.0:40.0 ForwardOrdered Regular Points
 10.0         11.0       12.0       13.0       14.0        15.0       16.0        17.0       …  32.0       33.0        34.0       35.0       36.0        37.0       38.0        39.0       40.0
  0.293347     0.737456   0.986853   0.780584   0.707698    0.804148   0.632667    0.780715      0.767575   0.555214    0.872922   0.808766   0.880933    0.624759   0.803766    0.796118   0.696768
  0.199599     0.290297   0.791926   0.564099   0.0241986   0.239102   0.0169679   0.186455      0.644238   0.467091    0.524335   0.42627    0.982347    0.324083   0.0356058   0.306446   0.117187
  ⋮                                                         ⋮                                ⋱                                     ⋮                                                        ⋮
  0.720404     0.388392   0.635609   0.430277   0.943823    0.661993   0.650442    0.91391   …   0.299713   0.518607    0.411973   0.410308   0.438817    0.580232   0.751231    0.519257   0.598583
  0.00602102   0.270036   0.696129   0.139551   0.924883    0.190963   0.164888    0.13436       0.717962   0.0452556   0.230943   0.848782   0.0362465   0.363868   0.709489    0.644131   0.801824

julia> A[Y=1:10, X=1]
10-element DimArray{Float64,1} with dimensions: 
  Y Sampled{Float64} 10.0:1.0:19.0 ForwardOrdered Regular Points
and reference dimensions: X
 10.0  0.293347
 11.0  0.737456
 12.0  0.986853
 13.0  0.780584
  ⋮    
 17.0  0.780715
 18.0  0.472306
 19.0  0.20442
```

[詳細についてはドキュメントを参照してください](https://rafaqz.github.io/DimensionalData.jl/stable)

DimensionalData.jlオブジェクトのいくつかの特性：

  * ブロードキャスティングとほとんどのBaseメソッドは、次元コンテキストを維持し、同期します。
  * Plots.jlのための包括的なプロットレシピ。
  * `DimTable`を持つTables.jlインターフェース
  * 一緒にインデックスでき、すべてのレイヤーに基本メソッドを適用できる多層の`DimStack`
  * GPUでの使用のためのAdapt.jlインターフェース、GPUカーネル引数としても使用可能。
  * 幅広い空間データ型を正確に処理するためのトレイト。

## インデックスまたはセレクタを含む次元を使用できるメソッド

`getindex`, `setindex!` `view`

## 次元、次元タイプ、または`Symbol`を使用して配列次元を示すことができるメソッド：

  * `size`, `axes`, `firstindex`, `lastindex`
  * `cat`, `reverse`, `dropdims`
  * `reduce`, `mapreduce`
  * `sum`, `prod`, `maximum`, `minimum`,
  * `mean`, `median`, `extrema`, `std`, `var`, `cor`, `cov`
  * `permutedims`, `adjoint`, `transpose`, `Transpose`
  * `mapslices`, `eachslice`

## `DimArray`を構築するために次元を使用できるメソッド：

  * `fill`, `ones`, `zeros`, `falses`, `trues`, `rand`

## **注意**：最近の変更により、エクスポートされたAPIが大幅に削減されました

以前にエクスポートされたメソッドは、移動されたサブモジュールを`using`することでグローバルスコープに持ち込むことができます - `LookupArrays`と`Dimensions`：

```julia
using DimensionalData
using DimensionalData.LookupArrays, DimensionalData.Dimensions
```

## 代替パッケージ

この分野には、同様のJuliaパッケージがたくさんあります。AxisArrays.jl、NamedDims.jl、NamedArrays.jlは、DimensionalData.jlが提供する機能の一部をカバーする登録された代替品です。DimensionalData.jlは、彼らの構文と機能のほとんどを再現できるはずです。

[AxisKeys.jl](https://github.com/mcabbott/AxisKeys.jl)や[AbstractIndices.jl](https://github.com/Tokazama/AbstractIndices.jl)は、他の興味深い開発の一部です。なぜこれほど多くの類似の選択肢があり、今後の方向性についての詳細は、この[スレッド](https://github.com/JuliaCollections/AxisArraysFuture/issues/1)を読んでください。

主な機能はここで説明されていますが、機能の完全なリストは[API](https://rafaqz.github.io/DimensionalData.jl/stable/api/)ページに記載されています。
