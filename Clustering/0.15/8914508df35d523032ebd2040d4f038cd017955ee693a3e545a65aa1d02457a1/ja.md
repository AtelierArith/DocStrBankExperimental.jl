```
silhouettes(assignments::Union{AbstractVector, ClusteringResult}, point_dists::Matrix) -> Vector{Float64}
silhouettes(assignments::Union{AbstractVector, ClusteringResult}, points::Matrix;
            metric::SemiMetric, [batch_size::Integer]) -> Vector{Float64}
```

与えられたクラスタリングに対する個々のポイントの*シルエット*値を計算します。

各個々のポイントに対するシルエット値の$n$長ベクトルを返します。

# 引数

  * `assignments::Union{AbstractVector{Int}, ClusteringResult}`: ポイントの割り当て（クラスタインデックス）のベクトル
  * `points::AbstractMatrix`: metricが何も指定されていない場合、ポイント間のペアワイズ距離の$n×n$行列であり、そうでない場合は$d$次元のクラスタ化されたデータポイントの$d×n$行列です。
  * `metric::Union{SemiMetric, Nothing}`: ポイント間の距離を計算するために使用される距離メトリックを示すDistances Metricオブジェクトのインスタンスまたは何も指定されていない。
  * `batch_size::Union{Integer, Nothing}`: 整数が指定されている場合、`batch_size`ポイントごとにバッチでシルエットを計算し、指定された`metric`によってバッチ計算がサポートされていない場合は`DimensionMismatch`をスローします。

# 参考文献

> Peter J. Rousseeuw (1987). *Silhouettes: a Graphical Aid to the Interpretation and Validation of Cluster Analysis*. Computational and Applied Mathematics. 20: 53–65. Marco Gaido (2023). Distributed Silhouette Algorithm: Evaluating Clustering on Big Data

