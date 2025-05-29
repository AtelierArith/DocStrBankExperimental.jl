```
OutcomeSpace
```

すべてのアウトカムスペース実装のスーパタイプです。

## 説明

ComplexityMeasures.jlでは、アウトカムスペースは可能な結果のセットを定義します $\Omega = \{\omega_1, \omega_2, \ldots, \omega_L \}$ （何らかの形の離散化）。文献では、アウトカムスペースはしばしば「アルファベット」とも呼ばれ、各アウトカムは「シンボル」または「イベント」と呼ばれます。

アウトカムスペースは、入力データを各アウトカム $\omega_i$ にマッピングするためのルールのセットも定義します。これは文献では *エンコーディング* または *シンボライズ* または *離散化* と呼ばれるプロセスです（[encodings](@ref encodings)を参照）。一部の [`OutcomeSpace`](@ref) は、離散化/エンコーディングの前にデータに変換（例えば、遅延埋め込み）を適用しますが、他の [`OutcomeSpace`](@ref) はデータを直接離散化/エンコードします。

## 実装

| アウトカムスペース                               | 原則            | 入力データ                     | カウント互換性 |
|:--------------------------------------- |:------------- |:------------------------- |:------- |
| [`UniqueElements`](@ref)                | ユニーク要素のカウント   | `Any`                     | ✔       |
| [`ValueBinning`](@ref)                  | ビニング（ヒストグラム）  | `Vector`, `StateSpaceSet` | ✔       |
| [`OrdinalPatterns`](@ref)               | 順序パターン        | `Vector`, `StateSpaceSet` | ✔       |
| [`SpatialOrdinalPatterns`](@ref)        | 空間内の順序パターン    | `Array`                   | ✔       |
| [`Dispersion`](@ref)                    | 分散パターン        | `Vector`                  | ✔       |
| [`SpatialDispersion`](@ref)             | 空間内の分散パターン    | `Array`                   | ✔       |
| [`CosineSimilarityBinning`](@ref)       | コサイン類似度       | `Vector`                  | ✔       |
| [`BubbleSortSwaps`](@ref)               | ソート時のスワップカウント | `Vector`                  | ✔       |
| [`SequentialPairDistances`](@ref)       | 逐次状態ベクトルの距離   | `Vector`, `StateSpaceSet` | ✔       |
| [`TransferOperator`](@ref)              | ビニング（転送演算子）   | `Vector`, `StateSpaceSet` | ✖       |
| [`NaiveKernel`](@ref)                   | カーネル密度推定      | `StateSpaceSet`           | ✖       |
| [`WeightedOrdinalPatterns`](@ref)       | 順序パターン        | `Vector`, `StateSpaceSet` | ✖       |
| [`AmplitudeAwareOrdinalPatterns`](@ref) | 順序パターン        | `Vector`, `StateSpaceSet` | ✖       |
| [`WaveletOverlap`](@ref)                | ウェーブレット変換     | `Vector`                  | ✖       |
| [`PowerSpectrum`](@ref)                 | フーリエ変換        | `Vector`                  | ✖       |

「入力データ」列では、入力の `eltype` が `<: Real` であると仮定しています。

## 使用法

アウトカムスペースは以下の入力として使用されます。

  * [`probabilities`](@ref)/[`allprobabilities_and_outcomes`](@ref) は確率質量関数を計算します。
  * [`outcome_space`](@ref) はアウトカムスペースの要素を返します。
  * [`total_outcomes`](@ref) はアウトカムスペースの基数を返します。
  * [`counts`](@ref)/[`counts_and_outcomes`](@ref)/[`allcounts_and_outcomes`](@ref) は確率の代わりに生のカウントを取得します（カウント互換性のあるアウトカムスペースのみ）。

## カウント互換性のあるアウトカムスペースと非カウント互換性のあるアウトカムスペース

アウトカムスペースには主に2つのタイプがあります。

  * カウント互換性のあるアウトカムスペースは、（エンコードされた）入力データの各ポイントが特定のアウトカム $\omega_i$ にマッピングされる頻度をカウントする明確な方法を持っています。これらのアウトカムスペースは、入力データを離散化するために [`encode`](@ref) を使用します。例としては、入力データを順序パターンにエンコードする [`OrdinalPatterns`](@ref) や、ポイントを規則的なグリッドに離散化する [`ValueBinning`](@ref) があります。以下の表は、どのアウトカムスペースがカウント互換性があるかを示しています。
  * 非カウント互換性のあるアウトカムスペースは、入力データの各ポイントが特定のアウトカム $\omega_i$ にマッピングされる頻度を明示的にカウントする明確な方法を持っていません。代わりに、これらのアウトカムスペースは、各アウトカム $\omega_i$ に対して1つの事前正規化された「相対カウント」のベクトルを返します。例としては、[`WaveletOverlap`](@ref) や [`PowerSpectrum`](@ref) があります。

カウント互換性のあるアウトカムスペースは、*任意の* [`ProbabilitiesEstimator`](@ref) と共に使用してカウントを確率質量関数に変換できます。非カウント互換性のあるアウトカムスペースは、最大尤度（[`RelativeAmount`](@ref)）確率推定器とのみ使用でき、これは各アウトカムの相対頻度によって確率を正確に推定します（形式的には、[`RelativeAmount`](@ref) 推定器もカウントを必要としますが、コードの一貫性のために相対頻度でも使用できるようにしています）。

関数 [`is_counting_based`](@ref) を使用して、アウトカムスペースがカウントに基づいているかどうかを確認できます。

## データからのアウトカムスペースの推定

一部のアウトカムスペースモデルは、入力の知識なしに $\Omega$ を推定できます（例：[`OrdinalPatterns`](@ref)）。他のアウトカムスペースは、$\Omega$ を具体的に指定するために入力データの知識を必要とします（例：[`ValueBinning`](@ref) と [`RectangularBinning`](@ref)）。もし `o` があるアウトカムスペースモデルで、`x` がある入力データであれば、[`outcome_space`](@ref)`(o, x)` は可能なアウトカム $\Omega$ を返します。$\Omega$ の基数を取得するには、[`total_outcomes`](@ref) を使用します。

## 実装の詳細

$$
\Omega
$$

の要素型はアウトカムスペースモデルによって異なりますが、*ハッシュ可能* で *ソート可能* であることが保証されています。これにより、特定のイベントのカウントを実験的実現を通じて便利に追跡することができます。アウトカムを辞書のキーとして使用し、そのキーの値としてカウントを使用するか、あるいはキーがアウトカムのままで、各実験的実現に対して1つの確率のベクトルを持つことができます。
