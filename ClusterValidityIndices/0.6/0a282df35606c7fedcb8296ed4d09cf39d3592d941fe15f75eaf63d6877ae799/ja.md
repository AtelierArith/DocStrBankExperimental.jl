```julia
get_cvi!(
    cvi::ClusterValidityIndices.CVI,
    sample::AbstractVector{T} where T<:Real,
    label::Integer
) -> Any

```

# 概要

基準値を逐次的に計算して返します。

このメソッドは、CVIオブジェクト、浮動小数点数のベクトルとしての単一サンプル、およびクラスタリングアルゴリズムによってサンプルに付与されたラベルを表す単一の整数を受け取ります。

!!! note
    CVIを逐次的に評価した後にバッチモードに切り替えることはできません。バッチで評価するには、新しいCVIオブジェクトを作成する必要があります。


# 引数

  * `cvi::CVI`: 基準値を提供するICVIの状態情報。
  * `sample::RealVector`: サンプルのクラスタリングに使用される特徴のベクトル。
  * `label::Integer`: クラスタリングアルゴリズムによってサンプルに付与されたクラスタラベル。

# 例

```julia
# 新しいCVIオブジェクトを作成
my_cvi = CH()

# 例としてランダムデータを読み込む; 特徴次元3のサンプル10個
dim = 3
n_samples = 10
data = rand(dim, n_samples)
labels = repeat(1:2, inner=n_samples)

# 各ステップで基準値を逐次的に計算して抽出
criterion_values = zeros(n_samples)
for ix = 1:n_samples
    sample = data[:, ix]
    label = labels[ix]
    criterion_values[ix] = get_icvi!(my_cvi, sample, label)
end
```

# メソッドリスト / 定義場所

```julia
get_cvi!(cvi, sample, label)
```

[`packages/ClusterValidityIndices/UT9rS/src/common.jl:392`](file:///home/terasaki/.julia/packages/ClusterValidityIndices/UT9rS/src/common.jl)で定義されています。
