```
parsimonyGF(net, tip_dictionary, criterion=:softwired)
parsimonyGF(net, species, sequenceData, criterion=:softwired)
```

離散的キャラクターを持つネットワークの最も節約的なスコアを計算します。これは、さまざまな節約基準（ソフトワイヤード（デフォルト）、ハードワイヤード、親など）を許可する一般的なフレームワーク（Van Iersel et al. 2018）を使用します。現時点ではソフトワイヤードのみが実装されています。

データは次のいずれかの形式で提供できます：

  * `tipdata`: 単一の特性のデータフレーム。この場合、分類群名は列1に表示されるか、「taxon」または「species」という名前の列に表示され、特性値は列2に表示されるか、「trait」という名前の列に表示されます。
  * `tipdata`: 単一の特性に対する辞書（分類群 => 状態）。
  * `species`: 文字列の配列、`sequences`: 種名の順序に対応する順序の配列。

## アルゴリズム

アルゴリズムの複雑さはネットワークのレベルに対して指数関数的であり、これは単一のブロブまたは二重接続成分内の最大ハイブリダイゼーションの数を意味します（Fischer et al. 2015）。関数は、ブロブ内の各ハイブリッドノードの小親のすべての状態割り当てをループするため、その複雑さは `n * m * c^2 * c^level` のオーダーであり、ここで `n` はティップの数、`m` は特性の数、`c` は状態の数です。

より高速なアルゴリズムについては [`parsimonysoftwired`](@ref) を参照してくださいが、ソフトワイヤード基準のみを解決します。

## 参考文献

1. Leo Van Iersel, Mark Jones, Celine Scornavacca (2017). Improved Maximum Parsimony Models for Phylogenetic Networks, Systematic Biology, (https://doi.org/10.1093/sysbio/syx094).
2. Fischer, M., van Iersel, L., Kelk, S., Scornavacca, C. (2015). On computing the Maximum Parsimony score of a phylogenetic network. SIAM J. Discrete Math., 29(1):559-585.

再帰的ヘルパー関数 [`parsimonyGF_bottomup!`](@ref) を使用してください。フィールド `ischild1`、`booln4` を使用してブロブのルートにあるノードを知り、`boole2` を使用してどのエッジが切断されているか（各ハイブリッドの小親の下）を知ります。
