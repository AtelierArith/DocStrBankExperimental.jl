```
parsimonysoftwired(net, tipdata)
parsimonysoftwired(net, species, sequences)
```

ネットワークのティップに与えられた離散的なキャラクターの最も節約的（MP）スコアを計算します。ソフトワイヤードパーシモニーの概念が使用されており、ネットワーク内に表示されるすべての木にわたって状態遷移の数が最小化されます。

データは次のいずれかの形式で与えることができます：

  * `tipdata`: 単一の特性のデータフレーム。この場合、分類群の名前は列1に表示されるか、「taxon」または「species」という名前の列に表示され、特性値は列2に表示されるか、「trait」という名前の列に表示されます。
  * `tipdata`: 単一の特性に対する辞書分類群 => 状態。
  * `species`: 文字列の配列、`sequences`: 種名の順序に対応する順序の配列。

## アルゴリズム

Fischer et al. (2015) による動的プログラミングアルゴリズムが使用されます。この関数は、ブロブ（双連結成分）内に表示されるすべての部分木をループ処理するため、その複雑さは `n * m * c^2 * 2^level` のオーダーであり、ここで `n` はティップの数、`m` は特性の数、`c` は状態の数、`level` はネットワークのレベル（ブロブ内の最大ハイブリダイゼーションの数）です。

異なるアルゴリズムについては、[`parsimonyGF`](@ref) を参照してください。これは遅いですが、他のパーシモニー基準に拡張可能です。

## 参考文献

1. Fischer, M., van Iersel, L., Kelk, S., Scornavacca, C. (2015). On computing the Maximum Parsimony score of a phylogenetic network. SIAM J. Discrete Math., 29(1):559-585.
