```julia
get_cvi!(
    cvi::ClusterValidityIndices.CVI,
    data::AbstractMatrix{T} where T<:Real,
    labels::AbstractVector{T} where T<:Integer
) -> Any

```

# 概要

バッチモードで基準値を計算して返します。

このメソッドは、CVIオブジェクト、浮動小数点数の行列としてのサンプルのバッチ、およびクラスタリングアルゴリズムによってデータに付与されたラベルを表す整数のベクトルを受け取ります。

!!! note
    バッチモードでCVIを評価した後にインクリメンタルモードに切り替えることはできません。インクリメンタルに評価するには、新しいCVIオブジェクトを作成する必要があります。


# 引数

  * `cvi::CVI`: 基準値を提供するCVIの状態情報。
  * `data::RealMatrix`: 外部クラスタリングプロセスで使用されるデータの行列。列はサンプル、行は特徴です。
  * `labels::IntegerVector`: 外部クラスタリングアルゴリズムによって`data`に付与されたラベルを表す整数のベクトル。

# 例

```julia
# 新しいCVIオブジェクトを作成
my_cvi = CH()

# 例としてランダムデータを読み込む; 特徴次元3の10サンプル
dim = 3
n_samples = 10
data = rand(dim, n_samples)
labels = repeat(1:2, inner=n_samples)

# バッチモードで最終基準値を計算
criterion_value = get_cvi!(cvi, data, labels)
```

# メソッドリスト / 定義場所

```julia
get_cvi!(cvi, data, labels)
```

[`packages/ClusterValidityIndices/UT9rS/src/common.jl:432`](file:///home/terasaki/.julia/packages/ClusterValidityIndices/UT9rS/src/common.jl)で定義されています。
