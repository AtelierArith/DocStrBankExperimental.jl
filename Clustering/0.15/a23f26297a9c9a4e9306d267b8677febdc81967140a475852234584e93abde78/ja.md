「ハード」クラスタリングの場合：

```
clustering_quality(data, centers, assignments; quality_index, [metric])
clustering_quality(data, clustering; quality_index, [metric])
```

「ファジー（ソフト）」クラスタリングの場合：

```
clustering_quality(data, centers, weights; quality_index, fuzziness, [metric])
clustering_quality(data, clustering; quality_index, fuzziness, [metric])
```

クラスタ中心を指定せずに「ハード」クラスタリングを行う場合：

```
clustering_quality(data, assignments; quality_index, [metric])
clustering_quality(data, clustering; quality_index, [metric])
```

データポイントとクラスタ中心を指定せずに「ハード」クラスタリングを行う場合：

```
clustering_quality(assignments, dist_matrix; quality_index)
clustering_quality(clustering, dist_matrix; quality_index)
```

与えられたクラスタリングの*品質指標*を計算します。

品質指標（実数値）を返します。

## 引数

  * `data::AbstractMatrix`: $d×n$ データ行列で、各列は1つの $d$ 次元データポイントを表します
  * `centers::AbstractMatrix`: $d×k$ 行列で、クラスタ中心が列として表されます
  * `assignments::AbstractVector{Int}`: $n$ ベクトルのポイント割り当て（クラスタインデックス）
  * `weights::AbstractMatrix`: $n×k$ 行列で、ファジークラスタリングの重みを持ち、`weights[i,j]` は $i$ 番目のデータポイントが $j$ 番目のクラスタに属する度合いです
  * `clustering::Union{ClusteringResult, FuzzyCMeansResult}`: クラスタリング手法の出力
  * `quality_index::Symbol`: 計算する品質指標；サポートされているオプションについては以下を参照してください
  * `dist_matrix::AbstractMatrix`: $n×n$ のペアワイズ距離行列；`dist_matrix[i,j]` は $i$ 番目と $j$ 番目のポイント間の距離です

## キーワード引数

  * `quality_index::Symbol`: 計算するクラスタリング*品質指標*；サポートされているオプションについては以下を参照してください
  * `fuzziness::Real`: クラスタリング*ファジネス* > 1
  * `metric::SemiMetric=SqEuclidean()`: メトリック/距離/類似性関数を定義する`SemiMetric`オブジェクト

`clustering_quality`を呼び出す際には、`centers`、`assignments`、および`weights`を明示的に指定するか、`clustering`を介して`ClusteringResult`を提供することができ、必要なデータが自動的に読み取られます。

クラスタ中心が不明なクラスタリングの場合、`data`ポイントは必要ありません。`dist_matrix`を明示的に提供することもできますが、そうでない場合は指定された`metric`を使用して`data`ポイントから計算されます。

## サポートされている品質指標

  * `:calinski_harabasz`: ハードまたはファジーのCalinski-Harabsz指標（↑）、クラスタ中心間の慣性とクラスタ内の慣性の修正比
  * `:xie_beni`: ハードまたはファジーのXie-Beni指標（↓）、クラスタ内の慣性とクラスタ中心間の最小距離の比
  * `:davies_bouldin`: Davies-Bouldin指標（↓）、クラスタと他の最も類似したクラスタとの類似性、すべてのクラスタで平均化
  * `:dunn`: Dunn指標（↑）、クラスタ間の最小距離と最大クラスタ直径の比
  * `:silhouettes`: 平均シルエット指標（↑）、[`silhouettes`](@ref)を参照

矢印 ↑ または ↓ は、クラスタリング品質の増加方向を指定します。クラスタリング品質指標の詳細については、[ドキュメント](@ref clustering_quality)を参照してください。
