```
pairalign(type, seq, ref, model, [options...])
```

2つの配列 `seq` と `ref` の間でペアワイズアライメントを実行します。

利用可能な `type` は次の通りです：

  * `GlobalAlignment()`
  * `LocalAlignment()`
  * `SemiGlobalAlignment()`
  * `OverlapAlignment()`
  * `EditDistance()`
  * `LevenshteinDistance()`
  * `HammingDistance()`

`GlobalAlignment`、`LocalAlignment`、`SemiGlobalAlignment`、および `OverlapAlignment` は、2つの配列間のアライメントスコアを最大化する問題です。したがって、`model` は `AbstractScoreModel` のインスタンスである必要があります（例：`AffineGapScoreModel`）。

`EditDistance`、`LevenshteinDistance`、および `HammingDistance` は、2つの配列間のアライメントコストを最小化する問題です。`EditDistance` の場合、`model` は `AbstractCostModel` のインスタンスである必要があります（例：`CostModel`）。`LevenshteinDistance` と `HammingDistance` には事前定義されたコストモデルがあるため、ユーザーはこれらのアライメントタイプに対してコストモデルを指定することはできません。

`pairalign` に `score_only=true` または `distance_only=true` オプションを渡すと、ペアワイズアライメントの結果はアライメントスコア/距離のみを保持します。これにより、フルアライメント結果を計算するよりも一部のアルゴリズムが高速に実行できる場合があります。他の利用可能な `options` は、各アライメントタイプのために文書化されています。

## 例

```
using BioSequences
using BioAlignments

# アフィンギャップスコアリングモデルを作成
affinegap = AffineGapScoreModel(
    match=5,
    mismatch=-4,
    gap_open=-5,
    gap_extend=-3
)

# 2つのDNA配列間でグローバルアライメントを実行
pairalign(GlobalAlignment(), dna"AGGTAG", dna"ATTG", affinegap)

# 2つのDNA配列間でローカルアライメントを実行
pairalign(LocalAlignment(), dna"AGGTAG", dna"ATTG", affinegap)

# LevenshteinDistance でコストモデルを指定することはできません
pairalign(LevenshteinDistance(), dna"AGGTAG", dna"ATTG")
```

参照： `AffineGapScoreModel`、`CostModel`
