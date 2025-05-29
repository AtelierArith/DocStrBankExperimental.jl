```
GP = partition_tree_fiedler(G::GraphSig; method::Symbol = :Lrw, swapRegion::Bool = true)
```

グラフのためのパーティションツリーを生成します。Fiedlerベクトルを使用して、L（非正規化ラプラシアン）またはL_rw（ランダムウォーク正規化ラプラシアン）のいずれかを使用します。

### 入力引数

  * `G::GraphSig`: 入力GraphSigオブジェクト
  * `method::Symbol`: パーティションツリーが構築された方法（デフォルト: :Lrw）
  * `swapRegion::Bool`: 子領域を部分グラフのエッジ重みの合計に基づいて入れ替えるかどうか（デフォルト: true）

### 出力引数

  * `GP::GraphPart`: 出力GraphPartオブジェクト

著作権 2015 カリフォルニア大学のRegenInt

実装者: Jeff Irion（アドバイザー: Dr. Naoki Saito）| 翻訳および修正: Naoki Saito, 2017年2月7日
